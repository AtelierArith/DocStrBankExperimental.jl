```
aws_mqtt5_listener_acquire(listener)
```

mqtt5 リスナーへの参照を追加します。

# 引数

  * `listener`: 参照を追加するリスナー

# 戻り値

リスナーオブジェクト

### プロトタイプ

```c
struct aws_mqtt5_listener *aws_mqtt5_listener_acquire(struct aws_mqtt5_listener *listener);
```
