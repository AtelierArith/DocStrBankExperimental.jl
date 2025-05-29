```
aws_http_proxy_negotiator_acquire(proxy_negotiator)
```

HTTPプロキシネゴシエーターへの参照を取得します

# 引数

  * `proxy_negotiator`: 参照を取得するネゴシエーター

# 戻り値

戦略

### プロトタイプ

```c
struct aws_http_proxy_negotiator *aws_http_proxy_negotiator_acquire(struct aws_http_proxy_negotiator *proxy_negotiator);
```
