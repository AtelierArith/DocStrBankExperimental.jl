```
lift(f, o1::Observables.AbstractObservable, rest...)
```

新しい `Observable` を作成するには、`f` を `o1` と `rest...` のすべてのオブザーバブルに適用します。初期値は最初の関数評価によって決まります。
