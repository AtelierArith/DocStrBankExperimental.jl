```
Prometheus.Summary(name, help; registry=DEFAULT_REGISTRY)
```

サマリーコレクタを構築します。

**引数**

  * `name :: String`: サマリーメトリックの名前。
  * `help :: String`: サマリーメトリックのドキュメント。

**キーワード引数**

  * `registry :: Prometheus.CollectorRegistry`: コレクタを登録するレジストリ。指定しない場合はデフォルトのレジストリが使用されます。登録をスキップするには `registry = nothing` を渡します。

**メソッド**

  * [`Prometheus.observe`](@ref observe(::Summary, ::Real)): サマリーに観測値を追加します。
  * [`Prometheus.@time`](@ref): セクションの時間を計測し、経過時間を観測値として追加します。
