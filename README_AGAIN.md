1.使用修改后的 mkpartmagna.sh 
1.1 wwn改为pci
1.2 /$ 改为 /boot
1.3 如果需要使用ssd journal + HDD的方式，需要修改journal的创建的命令

2.centos7去掉了pdsh，需要使用源码进行编译，编译时打开--with-ssh的支持
2.1 pdsh使用编译安装默认安装在/usr/local/bin目录下，需保证每个节点都安装此软件

3.注意ceph.conf文件的格式，必须保证以空行结束配置项

4.注意测试配置文件xxx.yaml的格式和关键字的准确
4.1 测试工具引用pool_profile的方式如下：
cluster:
  ...............
  pool_profiles:
    rados:
      pg_size: 128
      pgp_size: 128
      replication: 3
benchmarks:
  radosbench:
	.............
    pool_profile: 'rados'

5.centos需将/etc/sudoers文件中的Defaults requiretty注释掉

6.修改cbt工程文件中的killall为pkill

7.Test!