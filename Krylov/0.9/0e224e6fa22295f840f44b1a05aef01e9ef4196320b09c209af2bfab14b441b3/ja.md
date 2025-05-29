インプレースバージョンのGMRESに必要なベクトルを格納するための型。

外部コンストラクタ

```
solver = GmresSolver(m, n, memory, S)
solver = GmresSolver(A, b, memory = 20)
solver = GmresSolver(kc::KrylovConstructor, memory = 20)
```

これらのベクトルを作成するために使用できます。`memory`は、指定された値が`n`より大きい場合は`n`に設定されます。`memory`は、2番目のコンストラクタでのオプション引数です。
