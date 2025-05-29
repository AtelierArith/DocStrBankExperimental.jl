```
aws_io_library_init(allocator)
```

aws-c-ioで使用される内部データ構造を初期化します。aws-c-ioの機能を使用する前に呼び出す必要があります。

### プロトタイプ

```c
void aws_io_library_init(struct aws_allocator *allocator);
```
