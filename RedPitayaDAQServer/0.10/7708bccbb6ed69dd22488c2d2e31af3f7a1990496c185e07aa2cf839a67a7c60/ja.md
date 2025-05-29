```
receive(rp::RedPitaya, ch::Channel)
```

RedPitayaコマンドソケットから文字列を受信します。1行全体が受信されるまで読み取り、指定されたチャネル`ch`に入れます。
