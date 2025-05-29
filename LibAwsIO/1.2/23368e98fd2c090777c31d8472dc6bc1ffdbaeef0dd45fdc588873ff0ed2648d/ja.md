```
aws_event_loop_clean_up_base(event_loop)
```

```c++
 - テスト以外では使用しないでください。

 すべての実装に共通のクリーンアップコードです。
 これはイベントループ実装の *destroy() 関数からのみ呼び出されます。
 

```

### プロトタイプ

```c
void aws_event_loop_clean_up_base(struct aws_event_loop *event_loop);
```
