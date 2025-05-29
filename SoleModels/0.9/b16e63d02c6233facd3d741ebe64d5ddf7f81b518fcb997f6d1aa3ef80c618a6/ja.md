```
info!(m::AbstractModel, info::NamedTuple; replace::Bool=false)
info!(m::AbstractModel, key, val)
```

`m`内の`info`構造体を上書きします。

# キーワード引数

  * `replace::Bool`: info構造体全体を上書きします。

関連情報は[`AbstractModel`](@ref)、[`info`](@ref)を参照してください。
