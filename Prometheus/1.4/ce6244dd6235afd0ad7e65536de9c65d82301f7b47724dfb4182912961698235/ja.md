```
Prometheus.Histogram(name, help; buckets=DEFAULT_BUCKETS, registry=DEFAULT_REGISTRY)
```

ヒストグラムコレクタを構築します。

**引数**

  * `name :: String`: ヒストグラムメトリックの名前。
  * `help :: String`: ヒストグラムメトリックのドキュメント。

**キーワード引数**

  * `buckets :: Vector{Float64}`: ヒストグラムバケットの上限。バケットはソートされている必要があります。すでに含まれていない場合は、`Inf`が最後のバケットとして追加されます。デフォルトのバケットは `DEFAULT_BUCKETS = [0.005, 0.01, 0.025, 0.05, 0.075, 0.1, 0.25, 0.5, 0.75, 1.0, 2.5, 5.0, 7.5, 10.0, Inf]` です。
  * `registry :: Prometheus.CollectorRegistry`: コレクタを登録するレジストリ。指定しない場合はデフォルトのレジストリが使用されます。登録をスキップするには `registry = nothing` を渡します。

**メソッド**

  * [`Prometheus.observe`](@ref): ヒストグラムに観測を追加します。
  * [`Prometheus.@time`](@ref): セクションの時間を計測し、経過時間を観測として追加します。
