```
delay(b::CoroutineBehavior, millis)
```

`millis` ミリ秒間、動作をブロックします。

`block()` とは異なり、この関数は即座にブロックし、ブロックが期限切れになるまで再開しません。`Base.sleep()` とは異なり、この関数は動作のエージェントのロックを解除します。
