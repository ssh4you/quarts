#设置redis访问密码
#一、第一种方式 （当前这种linux配置redis密码的方法是一种临时的，如果redis重启之后密码就会失效，）

* 首先进入redis，如果没有开启redis则需要先开启：
```
[root@iZ94jzcra1hZ bin]# redis-cli -p 6379
127.0.0.1:6379> 
```
* 查看当前redis有没有设置密码：
```
127.0.0.1:6379> config get requirepass
"requirepass"
""
```
* 为以上显示说明没有密码，那么现在来设置密码：
```
127.0.0.1:6379> config set requirepass abcdefg
OK
127.0.0.1:6379>
``` 
* 再次查看当前redis就提示需要密码：
```
127.0.0.1:6379> config get requirepass
(error) NOAUTH Authentication required.
127.0.0.1:6379>
```
#二、第二种方式 （永久方式）
需要永久配置密码的话就去redis.conf的配置文件中找到requirepass这个参数，如下配置：

修改redis.conf配置文件　　
```
# requirepass foobared
requirepass 123   指定密码123
```
保存后重启redis就可以了