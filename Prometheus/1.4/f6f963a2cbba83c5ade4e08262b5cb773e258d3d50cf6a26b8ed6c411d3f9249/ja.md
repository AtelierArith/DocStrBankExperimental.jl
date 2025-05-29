```
Prometheus.Gauge(name, help; registry=DEFAULT_REGISTRY)
```

Gaugeコレクタを構築します。

**引数**

  * `name :: String`: gaugeメトリックの名前。
  * `help :: String`: gaugeメトリックのドキュメント。

**キーワード引数**

  * `registry :: Prometheus.CollectorRegistry`: コレクタを登録するレジストリ。指定しない場合はデフォルトのレジストリが使用されます。登録をスキップするには`registry = nothing`を渡します。

**メソッド**

  * [`Prometheus.inc`](@ref inc(::Gauge, ::Real)): gaugeの値を増加させます。
  * [`Prometheus.dec`](@ref): gaugeの値を減少させます。
  * [`Prometheus.set`](@ref): gaugeの値を設定します。
  * [`Prometheus.set_to_current_time`](@ref): gaugeの値を現在のユニックスタイムに設定します。
  * [`Prometheus.@time`](@ref): セクションの時間を計測し、gaugeの値を経過時間に設定します。
  * [`Prometheus.@inprogress`](@ref): 進行中の操作の数を追跡します。セクションに入るときにgaugeを増加させ、出るときに減少させます。
