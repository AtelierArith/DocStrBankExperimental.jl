```
aws_event_loop_start_destroy(event_loop)
```

```c++

 イベントループに破棄プロセスを開始するように信号を送ります。イベントループのこのAPIの実装が何かを行う場合、それは迅速でブロッキングしないものでなければなりません。ほとんどのイベントループ実装は、この関数のために空の実装を持っています。
 

```

### プロトタイプ

```c
void aws_event_loop_start_destroy(struct aws_event_loop *event_loop);
```
