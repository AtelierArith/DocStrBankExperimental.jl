```
Prometheus.GCCollector(; registry=DEFAULT_REGISTRY)
```

メトリクスを割り当てとガーベジコレクションに関する情報をエクスポートするコレクタを作成します。

**キーワード引数**

  * `registry :: Prometheus.CollectorRegistry`: コレクタを登録するレジストリ。デフォルトではデフォルトレジストリが使用されます。登録をスキップするには `registry = nothing` を渡します。

!!! note
    `GCCollector` はデフォルトレジストリに自動的に登録されます。必要に応じて、次のように呼び出すことで削除できます。

    ```julia
    Prometheus.unregister(Prometheus.DEFAULT_REGISTRY, Prometheus.GC_COLLECTOR)
    ```

