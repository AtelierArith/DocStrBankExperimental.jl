```
step!(sd::AbstractSimData)
```

シミュレーションを1フレームずつステップ実行することを可能にし、`sim!`に対してより手動的なアプローチを提供します。これは、ステップ間に他のプロセスを実行する必要がある場合や、シミュレーションの長さが可変である場合に便利です。`step!`はまた、`Output`の使用を排除し、必要に応じてグリッドデータの保存を手動で処理する必要があります。もちろん、出力は次のように手動で更新することもできます。

```julia
DynmicGrids.storeframe!(output, simdata)
```

`Output`の代わりに、内部の[`SimData`](@ref)オブジェクトが直接使用され、[`Extent`](@ref)オブジェクトと[`Ruleset`](@ref)を使用して定義できます。

# 例

```julia
using DynmicGrids, Plots
ruleset = Ruleset(Life(); proc=ThreadedCPU())
extent = Extent(; init=(a=A, b=B), aux=aux, tspan=tspan)
simdata = SimData(extent, ruleset)

# 単一ステップを実行し、更新された`SimData`オブジェクトを返します
simdata = step!(simdata)
# パディングなしでグリッドのビューを取得
grid = DynmicGrids.gridview(simdata[:a])
heatmap(grid)
```

この例は、`:a`グリッドの`GridData`オブジェクトを返し、それは`<: AbstractAray`です。
