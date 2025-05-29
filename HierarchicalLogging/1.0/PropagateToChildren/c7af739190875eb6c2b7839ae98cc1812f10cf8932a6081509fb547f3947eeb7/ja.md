```
PropagateToChildren.Mode
```

`logger`がメッセージを受信したとき、それがどのように子に伝播されるかを決定します。

  * `PropagateToChildren.AllChildren`: メッセージを`logger`のすべての子に伝播します
  * `PropagateToChildren.DirectChildren`: メッセージを直接の子にのみ伝播します（例：`logger` "A.B" がメッセージを受信した場合、"A.B.C"（存在する場合）に転送されますが、"A.B.C.D"には転送されません）
  * `PropagateToChildren.None`: メッセージを子のロガーに伝播しません
