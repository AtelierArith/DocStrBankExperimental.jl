```
RemoteException(captured)
```

リモート計算での例外はキャプチャされ、ローカルで再スローされます。`RemoteException`はワーカーの`pid`とキャプチャされた例外をラップします。`CapturedException`はリモート例外と、例外が発生したときのコールスタックのシリアライズ可能な形式をキャプチャします。
