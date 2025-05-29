```
logparam(instance::MLFlow, run_id::String, key::String, value::String)
logparam(instance::MLFlow, run::Run, key::String, value::String)
logparam(instance::MLFlow, run_id::String, param::Param)
logparam(instance::MLFlow, run::Run, param::Param)
```

[`Run`](@ref)に使用される[`Param`](@ref)をログします。[`Param`](@ref)はキーと値のペア（文字列キー、文字列値）です。例としては、MLモデルのトレーニングに使用されるハイパーパラメータや、ETLパイプラインで使用される定数の日付や値が含まれます。[`Param`](@ref)は[`Run`](@ref)に対して一度だけログできます。

# 引数

  * `instance`: [`MLFlow`](@ref)の設定。
  * `run_id`: [`Param`](@ref)をログする[`Run`](@ref)のID。
  * `key`: [`Param`](@ref)の名前。
  * `value`: ログされる[`Param`](@ref)の文字列値。

# 戻り値

成功した場合は`true`を返します。それ以外の場合は例外を発生させます。
