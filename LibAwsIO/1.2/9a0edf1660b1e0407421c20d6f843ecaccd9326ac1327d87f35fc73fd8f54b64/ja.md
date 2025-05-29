```
aws_event_loop_get_impl(event_loop)
```

```c++
 - テスト以外では使用しないでください。

 イベントループの不透明な内部ユーザーデータを返します。特権のある消費者によって特定の実装にキャストできます。
 

```

### プロトタイプ

```c
void *aws_event_loop_get_impl(struct aws_event_loop *event_loop);
```
