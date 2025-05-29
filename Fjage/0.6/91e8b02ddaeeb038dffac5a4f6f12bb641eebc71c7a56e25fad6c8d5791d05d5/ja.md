```
block(b::Behavior)
block(b::Behavior, millis)
```

動作をブロックとしてマークし、`restart(b)`を使用して再起動されるまで実行を防ぎます。`millis`が指定されている場合、動作は`millis`ミリ秒後に自動的に再起動されます。
