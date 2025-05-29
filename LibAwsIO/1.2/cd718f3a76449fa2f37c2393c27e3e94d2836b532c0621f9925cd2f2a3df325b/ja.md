```
aws_event_loop_complete_destroy(event_loop)
```

```c++

 イベントループが破棄プロセスを完了するのを待ちます。 この関数がデッドロックしないためには、以前に aws_event_loop_start_destroy() が呼び出されている必要があります。
 

```

### プロトタイプ

```c
void aws_event_loop_complete_destroy(struct aws_event_loop *event_loop);
```
