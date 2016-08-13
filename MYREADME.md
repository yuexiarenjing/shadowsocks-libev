#Configure shadowsocks
Install python3
```
wget https://www.python.org/ftp/python/3.4.3/Python-3.4.3.tgz
tar -xf Python-3.4.3.tgz 
cd Python-3.4.3/
./configure
make
make install
```
Install pip
```
wget --no-check-certificate https://github.com/pypa/pip/archive/1.5.5.tar.gz
tar zvxf 1.5.5.tar.gz    
cd pip-1.5.5/
python setup.py install
```
Install shadowsocks
```
pip install shadowsocks
ssserver -h
```
Create a configuration file
```
#/root
vim config.json
#add
# 注释版配置
{
    "server":"servier_ip",   # 服务器IP
    "server_port":65432,     # ss服务器所使用的端口号，建议改到30000-60000
    "password":"password",   # ss服务器密码，轻易不要分享
    "timeout":60,            # 超时时间，建议设置为60
    "method":"rc4-md5"         # 加密方式，需要和客户端配合设置
}
```
Reboot configuration
```
vim /etc/rc.d/rc.local
#add a new line
/usr/local/bin/ssserver -c /root/config.json -d start --pid-file /tmp/ss.pid --log-file /tmp/ss.log
```
