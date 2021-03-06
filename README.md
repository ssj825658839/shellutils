# shellutils


#### NetworkSpeedTest 使用说明

  本脚本可以用来测试某台服务器到目标服务器之间的scp网络传输速度。

```
"-m 输入用户名"	
"-i 输入IP地址" 
"-p 输入端口号(默认为80)" 
"-n 输入发送次数(默认为5)" 
"-b 输入发送文件大小(默认为20M)"
```
> 注意事项

>1. 必须有-m -i 参数

>2. 在目标服务器上必须有本地公钥,且验证ssh-key可登陆成功.

>3. 参数输入顺序请按照以上顺序,否则会导致参数无效.

>4. 保证当前用户对该文件有可执行权限.

>5. 网速测试过程中,请不要试图使用`crtl+c`推出,否则会导致测试结果异常

>6. 单次发送文件大小不宜过大,需考虑磁盘储存问题,建议使用者多次发送小文件.


#### LogSearchByCod使用说明


本脚本可以根据特定的条件循环检索文件。此脚本尚不完善，需要有一定shell基础的人方可使用。


```
echo "-p 检索语句前缀 "	
echo "-s 检索语句后缀 "	
echo "-t 检索文件存放路径"
echo "-c 检索语句中条件变量池文件路径，条件以行区分" 
```

例如：
```
sudo ./logalsearchtool.sh -p "cat /home/deploy/text.log.2018-* |grep 2018-07-01 | grep openNews |  grep '\"channel\":\"china\"' "  -s "wc -l" -t /home/deploy/data/log.csv -c /home/deploy/ids.txt
```

>注意

>1.此检索变量目前只支持grep，脚本中将前缀和后缀中间加了一个`| grep $cod | ` 的管道过滤。

>2.此脚本需使用sudo权限执行

>3.传递带`""`的参数时候需要使用转义字符`\`
