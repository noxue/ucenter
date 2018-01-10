## Ucenter Client For Laravel5

运行命令：
~~~
composer require noxue/ucenter:v1.1
~~~

安装完后，在 `app/config/app.php` 文件中找到 `providers` 键，

~~~
'providers' => [

    'Noxue\Ucenter\UcenterServiceProvider'

]
~~~

找到 `aliases` 键，

~~~
'aliases' => [

    'Ucenter' => 'Noxue\Ucenter\Facades\Ucenter'

]
~~~

## 配置文件
运行以下命令发布配置文件

创建 `config/ucenter.php` 写入以下内容：

```
<?php

/**
 * 为了方便，直接修改以下带【*】的配置即可
 */

return [
    'url'            => env('UC_URL', ''),  //这里是你的项目所在的接口api的前缀，比如 /xx/api/uc 一般直接留空。
    'connect'        => env('UC_CONNECT', null), //这里可以是 mysql或者null，null会通过socket远程请求接口的方式通信
    'dbhost'         => env('UC_DBHOST', 'localhost'),
    'dbuser'         => env('UC_DBUSER', 'root'),
    'dbpw'           => env('UC_DBPW', 'root'),
    'dbname'         => env('UC_DBNAME', 'ucenter'),
    'dbcharset'      => env('UC_DBCHARSET', 'utf8'),
    'dbtablepre'     => env('UC_DBTABLEPRE', '`ucenter`.uc_'),
    'dbconnect'      => env('UC_DBCONNECT', '0'),
    'key'            => env('UC_KEY', 'asflkhKFJHGH5648asdfasdfhj9845613asdf'),  //这个是通信密钥，必须和服务端统一【*】
    'api'            => env('UC_API', 'http://dz.noxue.cn/uc_server'),                  //这个是uc_server的服务端地址【*】
    'ip'             => env('UC_IP', '127.0.0.1'),
    'charset'        => env('UC_CHARSET', 'utf-8'),
    'appid'          => env('UC_APPID', '1'),   //这里是应用编号
    'ppp'            => env('UC_PPP', '20'),

    //这里是uc_server调用你的程序的接口，配置成uc的话，将会和前面的UC_URL配置一起形成这样的地址 url/api/uc
    'apifilename'    => env('UC_APIFILENAME', 'uc'),

    //这里如果要异步登陆，可以直接继承这个类实现其中的方法，也可以创建app/Service/Ucenter.php(文件放哪里都可以，这里只是推荐) 实现该类实现的接口【*】
    'service'        => env('UC_SERVICE', 'Noxue\Ucenter\Services\Api'),
];

```

## 路由

在`routes/web.php`中写入:

`Ucenter::routes();`

这个会添加一个api地址，用于同步登陆和退出

## 使用
例如：获取用户名为admin的信息
~~~
$result = Ucenter::uc_get_user('admin');
var_dump($result);
~~~

有任何疑问请到此处提问：http://www.noxue.com/f-wenda-1.html

## 联系我
有问题，请提交issue
