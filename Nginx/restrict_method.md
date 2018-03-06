# Nginxで許可するメソッドを制限する方法

## limit_exceptで簡単に許可するメソッドを制限できる

```nginx
location / {
    limit_except GET HEAD POST { deny all; }
}
```

## 複数locationに設定したい場合

serverディレクティブにこのように書いてあげると良い

```nginx
        if ($request_method !~ ^(GET|HEAD|POST)$ ) {
                return 444;
        }
```

## 参考

- <http://nginx.org/en/docs/http/ngx_http_core_module.html#limit_except>
