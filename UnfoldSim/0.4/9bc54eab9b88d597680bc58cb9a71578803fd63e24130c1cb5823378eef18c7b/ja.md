```
UniformOnset <: AbstractOnset
```

イベント間距離（サンプル単位）のための一様分布を提供します。

ヒント: イベント間距離のサンプルを手動で生成するには、[`simulate_interonset_distances`](@ref) 関数を使用してください。

# フィールド

  * `width = 50`（オプション）: 一様分布の幅（=> "ジッター"）。下限が0であるため、`width`は上限でもあります。
  * `offset = 0`（オプション）: イベント間の最小距離。最大距離は `offset + width` です。

# 例

```julia-repl
julia> onset_distribution = UniformOnset(width = 25, offset = 5)
UniformOnset
  width: Int64 25
  offset: Int64 5
```

他に [`LogNormalOnset`](@ref)、[`NoOnset`](@ref) も参照してください。
