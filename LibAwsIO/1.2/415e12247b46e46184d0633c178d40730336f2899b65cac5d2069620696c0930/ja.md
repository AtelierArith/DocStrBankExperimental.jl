```
aws_event_loop_new_base(allocator, clock, vtable, impl)
```

```c++
 - テスト以外では使用しないでください。

 テスト指向のオーバーライドを使用して、すべてのイベントループ実装で使用される基本構造を初期化します。
 

```

### プロトタイプ

```c
struct aws_event_loop *aws_event_loop_new_base( struct aws_allocator *allocator, aws_io_clock_fn *clock, struct aws_event_loop_vtable *vtable, void *impl);
```
