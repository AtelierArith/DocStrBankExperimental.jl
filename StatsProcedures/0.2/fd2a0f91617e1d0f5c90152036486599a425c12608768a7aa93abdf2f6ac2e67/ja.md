```
proceed(sps::AbstractVector{<:StatsSpec}; kwargs...)
```

`sps`内の[`StatsSpec`](@ref)に対して手続きを実行し、[`StatsSpec`](@ref)に対して同一のステップを繰り返さないようにします。[`@specset`](@ref)も参照してください。

# キーワード

  * `verbose::Union{Bool,IO}=false`: 呼び出されたときに各ステップの名前を`stdout`または指定された`IO`ストリームに印刷します。
  * `keep=nothing`: 返される追加オブジェクトの名前（`Symbol`型）。
  * `keepall::Bool=false`: [`StatsSpec`](@ref)からの引数とともに手続きによって生成されたすべてのオブジェクトを返します。
  * `pause::Int=0`: 指定されたステップ数を終了した後に[`StatsStep`](@ref)の反復を中断します（デバッグ用）。

# 戻り値

  * `Vector`: `sps`の同じ順序で各仕様の結果。

デフォルトでは、対応する手続きの専用結果オブジェクトまたは最後の[`StatsStep`](@ref)によって返された最後の値が、各[`StatsSpec`](@ref)の返される`Vector`の要素になります。`keep`または`keepall`のいずれかが指定されると、各[`StatsSpec`](@ref)に対して追加オブジェクトを持つ`NamedTuple`が形成されます。
