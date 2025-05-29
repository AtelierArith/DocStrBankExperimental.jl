`pomp` は *PompObject* クラスのコンストラクタです。

```
pomp(
    data;
    t0, times, timevar,
    params,
    accumvars,
    rinit, rprocess,
    rmeasure, logdmeasure
    )
```

## 引数

  * `data`: 観測値。デフォルトのコンストラクタは、NamedTuples のベクターをデータとして受け取ります。また、DataFrame を提供することもできます。
  * `t0`: ゼロ時間、t₀。
  * `times`: 観測時間。`data` が DataFrame として提供される場合、`times` は DataFrame 内の時間変数であるシンボルである必要があります。
  * `timevar`: オプションのシンボル。時間変数の名前。
  * `params`: パラメータ。NamedTuple または NamedTuples のベクター。
  * `accumvars`: 各シミュレーションステージの直前にリセットされる状態変数の NamedTuple（通常はゼロに設定されます）。
  * `rinit`: t₀ における潜在状態分布のシミュレーター。このコンポーネントは、パラメータとオプションで `t0`（初期時間）を受け取る関数である必要があります。
  * `rprocess`: 潜在状態プロセスのシミュレーター。このコンポーネントはプラグインである必要があります（[`euler`](@ref)、[`onestep`](@ref)、および [`discrete_time`](@ref) を参照）。
  * `rmeasure`: 測定プロセスのシミュレーター。このコンポーネントは、状態、パラメータ、およびオプションで `t`（現在の時間）を受け取る関数である必要があります。
  * `logdmeasure`: 測定プロセスの対数 pdf。このコンポーネントは、データ、状態、パラメータ、およびオプションで `t`（現在の時間）を受け取る関数である必要があります。
