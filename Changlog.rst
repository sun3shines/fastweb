version 1.4.0:
    update: fastweb.loader.load_manager -> fastweb.loader.load_component
    fix: 修复mysql注入问题
    fix: 修复异步重试机制
    fix: 修复断开连接后的重新连接
    fix: 修复query后需要commit操作
    fix: 修复配置文件数字转换从float更改成int,解决数据库数字字符串问题
    fix: mysql防注入修复
    add: 增加handler级别线程池，处理阻塞操作
    fix: mysql.ping 使用reconnect参数，当连接没有断开时会报错(2003, "Can't connect to MySQL server on 'x.x.x.x' (fd x already registered)").
         该错误并非一个致命错误，只是一个警告


version 1.4.1:
    update: fastweb.loader.load_configuration 只用来加载非组件类的配置文件，这些配置是在业务中需要使用的
    update: fastweb.loader.load_component 用来加载制定配置文件中的组件，只会进行组件的加载，非组件的配置会被忽略掉，可以多次的加载不同的配置，以满足大量组件写在不同的配置文件中
            以上两条是为了配置文件的分离，使它们在物理上就是隔离的，防止混淆
    update: fastweb.web.start_server -> fastweb.web.start_web_server
    add: 增加依赖celery的任务系统，包括worker的运行和通过web层调用任务，具体参看fastweb.task和examples.task


version 1.4.1.1
    fix: 修复同步调用系统命令函数，原采用subprocess调用系统命令，每次都需要创建子进程，面对大并发情况，性能较差