```
aws_http_proxy_strategy_acquire(proxy_strategy)
```

HTTPプロキシ戦略への参照を取得します

# 引数

  * `proxy_strategy`: 参照を取得する戦略

# 戻り値

戦略

### プロトタイプ

```c
struct aws_http_proxy_strategy *aws_http_proxy_strategy_acquire(struct aws_http_proxy_strategy *proxy_strategy);
```
