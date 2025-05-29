```
ThreadSafeDict(pairs::Vector{Pair{K,V}})
```

ThreadSafeDictのための構造体とコンストラクタ。Dict構造体ごとに1つのロックがあります。すべての関数はこのロックをロックし、dメンバーDictに引数を渡し、スピンロックのロックを解除し、その後Dictによって返されるものを返します。
