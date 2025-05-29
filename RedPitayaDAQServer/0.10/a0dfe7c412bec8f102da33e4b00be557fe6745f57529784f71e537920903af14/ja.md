```
sequence!(rp::RedPitaya, seq::AbstractSequence)
```

クライアント側の表現 `seq` をサーバーに送信し、現在のシーケンスのリストに追加します。必要なコマンドが成功した場合は `true` を返します。
