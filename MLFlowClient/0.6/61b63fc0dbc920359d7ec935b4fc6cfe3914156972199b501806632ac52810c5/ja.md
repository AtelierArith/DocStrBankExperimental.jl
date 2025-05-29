```
logmetric(instance::MLFlow, run_id::String, key::String, value::Float64;
    timestamp::Int64=round(Int, now() |> datetime2unix),
    step::Union{Int64, Missing}=missing)
logmetric(instance::MLFlow, run::Run, key::String, value::Float64;
    timestamp::Int64=round(Int, now() |> datetime2unix),
    step::Union{Int64, Missing}=missing)
```

[`Run`](@ref)のために[`Metric`](@ref)をログします。[`Metric`](@ref)は、関連するタイムスタンプを持つキーと値のペア（文字列キー、浮動小数点値）です。例としては、MLモデルの精度を表すさまざまなメトリックが含まれます。[`Metric`](@ref)は複数回ログすることができます。

# 引数

  * `instance`: [`MLFlow`](@ref)の設定。
  * `run_id`: [`Metric`](@ref)をログする[`Run`](@ref)のID。
  * `key`: [`Metric`](@ref)の名前。
  * `value`: ログされる[`Metric`](@ref)のダブル値。
  * `timestamp`: [`Metric`](@ref)がログされた時のミリ秒単位のUnixタイムスタンプ。
  * `step`: [`Metric`](@ref)をログするステップ。

# 戻り値

成功した場合は`true`。そうでない場合は例外を発生させます。
