```
receive(rp::RedPitaya, timeout::Number)
```

RedPitayaコマンドソケットから文字列を受信します。完全な行が受信されるまで、またはタイムアウト秒が経過するまで読み取ります。後者の場合、エラーがスローされます。
