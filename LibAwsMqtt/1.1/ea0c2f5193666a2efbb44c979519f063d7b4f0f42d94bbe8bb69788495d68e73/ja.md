```
aws_mqtt5_listener_release(listener)
```

mqtt5 リスナーへの参照を削除します。参照カウントがゼロになると、リスナーの非同期破棄が開始されます。

# 引数

  * `listener`: 参照を削除するリスナー

# 戻り値

NULL

### プロトタイプ

```c
struct aws_mqtt5_listener *aws_mqtt5_listener_release(struct aws_mqtt5_listener *listener);
```
