```
SingleConfigMax{K, BOUNDED} <: AbstractProperty
SingleConfigMax(k::Int; bounded=false)
```

最大Kサイズの単一解を見つけること、例えば[`IndependentSet`](@ref)問題の場合、それは最大独立集合の1つです。

  * 対応するデータ型は、`BOUNDED`が`false`の場合は[`CountingTropical{Float64,<:ConfigSampler}`](@ref)、それ以外の場合は[`Tropical`](@ref)です。
  * 重み付き制約充足問題がサポートされています。
  * GPUがサポートされています。

## キーワード引数

  * `bounded`がtrueの場合、中間構成を保存するための作業メモリを削減するためにバウンディングトリック（またはブール勾配）を使用します。
