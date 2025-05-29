```
PrunedFIsBackend <: StochasticAD.AbstractFIsBackend
```

衝突したとき（例えば、加算されたとき）に摂動の間でプルーニングを行うバックエンドアルゴリズムです。現在はすべての摂動の中から均等に選択します。
