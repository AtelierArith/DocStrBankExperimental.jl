```
aws_channel_new(allocator, creation_args)
```

新しいチャネルを割り当てます。特に指定がない限り、チャネルおよびチャネルスロットのすべての関数は、そのチャネルのイベントループのスレッド内で実行する必要があります。channel_optionsはコピーされます。

### プロトタイプ

```c
struct aws_channel *aws_channel_new(struct aws_allocator *allocator, const struct aws_channel_options *creation_args);
```
