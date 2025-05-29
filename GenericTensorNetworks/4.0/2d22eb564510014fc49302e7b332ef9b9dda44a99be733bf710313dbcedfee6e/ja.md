```
SingleConfigMin{K, BOUNDED} <: AbstractProperty
SingleConfigMin(k::Int; bounded=false)
```

最小のKサイズを持つ単一の解を見つける。

  * 対応するデータ型は、`BOUNDED`が`false`の場合は逆[`CountingTropical{Float64,<:ConfigSampler}`](@ref)、それ以外の場合は逆[`Tropical`](@ref)です。
  * 重み付き制約充足問題がサポートされています。
  * GPUがサポートされています。

## キーワード引数

  * `bounded`がtrueの場合、作業メモリを中間構成を保存するために減らすためにバウンディングトリック（またはブール勾配）を使用します。
