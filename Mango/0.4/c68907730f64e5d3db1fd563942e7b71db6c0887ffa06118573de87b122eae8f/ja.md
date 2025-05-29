```
forward_to(agent, content, forward_to_address, received_meta; kwargs...)
```

メッセージを特定のエージェントに転送し、メッセージの処理時に受信したメタデータを使用します。このメソッドは基本的に、与えられた入力に対してsend_messageを呼び出すだけですが、メッセージを転送されたものとしてマークするために、正しいメタデータフィールドを追加して埋めます。

これには、次のメタデータが設定されます。

  * 'forwarded=true',
  * 'forwarded*from*address=元の送信者のアドレス',
  * 'forwarded*from*id=元の送信者のID'
