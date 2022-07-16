# This is the main things I need

https://www.jianshu.com/p/9a237f8c2314?u_atoken=85595321-462d-47fa-9224-dbdc5e2ab263&u_asession=01ZRu8yO66onT-gDaDsJpY6JH5sUDTcgcRy4CUc_OPEhkuvekw--46xekYVIF0BFCwX0KNBwm7Lovlpxjd_P_q4JsKWYrT3W_NKPr8w6oU7K-ImSYzaW5fhdgbhEkcwwj5MKWrbBzYAhXhkL4v5_cjQmBkFo3NEHBv0PZUm6pbxQU&u_asig=05IBWrYtfymA_uDUcLVJ8xTWVNycaW9n_GRsF47Z5bH1vnel9lFO6GPxJ2OEd86pBLZQ6xXJmARr_rTTwVA8AsIj2wL1cJz7ZVqWbsYYD7f16OQCIewmmGIJZklzfvmD-Mx9hOpUf7tZrNWLjZuU7XA75ZanQ_j7znEkKEyIef-UH9JS7q8ZD7Xtz2Ly-b0kmuyAKRFSVJkkdwVUnyHAIJzbims1EUQPlNJUXuPB9Gqjq8-g6P8YX9dRaJ2p5RynWSdf9JIAkyKervFWgmMgV8j-3h9VXwMyh6PgyDIVSG1W-414zJaIuBr1MMC1yYTT0F9DF7TKnKQYEk6HFWwBQz79neGwOIEh2n3yieIIpXCzDi6I_e414d4cz8_z_Z9CVAmWspDxyAEEo4kbsryBKb9Q&u_aref=qwH08FwmNSM5C3ZSd6K%2FxiyygqI%3D

# To do the compilation, you need to do the following things

## First, install hadoop on your computer

## Second, modify the ldconfig files
```shell
vim /etc/ld.so.conf

# add the following sentence
#
/hadoop-dir/lib/native
```
## Third, add the following things into your ~/.bashrc

Remember that, you need to add the content into all users.

```shell
export HADOOP_HOME=/home/hadoop/hadoop-3.2.3
export HADOOP_INSTALL=$HADOOP_HOME
export HADOOP_MAPRED_HOME=$HADOOP_HOME
export HADOOP_COMMON_HOME=$HADOOP_HOME
export HADOOP_HDFS_HOME=$HADOOP_HOME
export YARN_HOME=$HADOOP_HOME
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"
JAVA_HOME=/usr/lib/jvm/default-java/
#LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jvm/default-java/lib/server:/usr/lib/jvm/default-java/lib/amd64/
export LD_LIBRARY_PATH=$JAVA_HOME/lib/server
export CLASSPATH=`hadoop classpath`

```

## Lastly, compile your file by the following words

gcc your_file.c -I$HADOOP_HOME/include -L$HADOOP_HOME/lib/native -lhdfs 
