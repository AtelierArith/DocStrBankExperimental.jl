モデルパラメータの型。

# フィールド:

  * `name::String`: パラメータの名前。
  * `value::Float64`: パラメータの現在の値。
  * `lower_bound::Float64`: 下限。
  * `upper_bound::Float64`: 上限。
  * `vary::Bool`: 最適化中にパラメータを変化させるかどうか。

# コンストラクタ:

```
Parameter(;name=nothing, value::Real, lower_bound::Real=-Inf, upper_bound::Real=Inf, vary::Bool=true)
```

新しいパラメータを構築します。パラメータ名は提供する必要はなく、辞書インターフェースを使用する場合は自動的に設定されます。
