```
aws_event_loop_destroy(event_loop)
```

```c++
 - テスト以外では使用しないでください。

 イベントループの実装を破棄します。
 イベントループがまだ実行中の状態である場合、この関数はイベントループのシャットダウンを待機するためにブロックします。
 イベントループが複数のスレッドによって共有されている場合、破棄は正確に1つのスレッドによって呼び出されなければなりません。他のすべてのスレッドは、破棄の呼び出しの前にイベントループへのAPI呼び出しが行われることを確認しなければなりません。

 内部的には、これは aws_event_loop_start_destroy() を呼び出し、その後 aws_event_loop_complete_destroy() を呼び出します。
 
```

### プロトタイプ

```c
void aws_event_loop_destroy(struct aws_event_loop *event_loop);
```
