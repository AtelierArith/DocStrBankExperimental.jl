```
Prometheus.Counter(name, help; registry=DEFAULT_REGISTRY)
```

カウンターコレクタを構築します。

**引数**

  * `name :: String`: カウンタメトリックの名前。
  * `help :: String`: カウンタメトリックのドキュメント。

**キーワード引数**

  * `registry :: Prometheus.CollectorRegistry`: コレクタを登録するレジストリ。指定しない場合はデフォルトのレジストリが使用されます。登録をスキップするには `registry = nothing` を渡します。

**メソッド**

  * [`Prometheus.inc`](@ref): カウンタをインクリメントします。
