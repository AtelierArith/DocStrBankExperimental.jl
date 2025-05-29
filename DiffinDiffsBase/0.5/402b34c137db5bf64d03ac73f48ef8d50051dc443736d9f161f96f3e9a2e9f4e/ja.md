```
post!(f, ::StataPostHDF, r::AbstractDIDResult; kwargs...)
```

結果 `r` を Stata モジュール [`posthdf`](https://github.com/junyuan-chen/posthdf) にエクスポートします。`r` からのフィールド値のサブセットが、キーと値のペアを設定することによって `f` に配置されます。`f` は `HDF5.Group` であるか、文字列でインデックス付けできる任意のオブジェクトであることができます。

# キーワード

  * `model::String=repr(typeof(r))`: モデルの名前。
  * `fields::Union{AbstractVector{<:Union{Symbol, Pair{String,Symbol}}}, Nothing}=nothing`: エクスポートされる追加のフィールド；代替名は `Pair` を使って指定できます。
  * `at::Union{AbstractVector{<:Real}, Bool, Nothing}=nothing`: Stata に `at` ベクターを投稿します。
