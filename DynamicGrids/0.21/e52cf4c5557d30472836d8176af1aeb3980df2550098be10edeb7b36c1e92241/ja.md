```
SetCellRule <: Rule
```

任意のセルに手動で書き込むことができるルールの抽象スーパタイプです。

例えば、`SetCellRule`は次のように適用され、現在のセルに単純に1を加えます：

```jldoctest SetCellRule
using DynamicGrids
struct MySetCellRule{R,W} <: SetCellRule{R,W} end

function applyrule!(data::AbstractSimData, rule::MySetCellRule{R,W}, state, I) where {R,W}
    # セル10上および10横に1を加える
    I, isinbounds = inbounds(I .+ 10)
    isinbounds && add!(data[W], 1, I...)
    return nothing
end
# output
applyrule! (generic function with 1 method)
```

`!`バンガーに注意してください - このメソッドは`data`の状態を変更します。

グリッドを更新するには、原子演算子[`add!`](@ref)、[`sub!`](@ref)、[`min!`](@ref)、[`max!`](@ref)、および[`and!`](@ref)、[`or!`](@ref)を`Bool`に対して使用できます。これらのメソッドは、すべてのグリッドセルからの書き込みを安全に組み合わせます - `setindex!`を直接使用するとバグが発生します。

複数の書き込みグリッドがある場合は、型パラメータからグリッドキーを取得する必要があります。ここでは`W1`と`W2`です：

```jldoctest SetCellRule
function applyrule(data, rule::MySetCellRule{R,Tuple{W1,W2}}, state, I) where {R,W1,W2}
    add!(data[W1], 1, I...)
    add!(data[W2], 2, I...)
    return nothing
end
# output
applyrule (generic function with 1 method)
```

DynamicGridsは次のことを保証します：

  * グリッド上のどこに書き込まれた値は、同じタイムステップで同じルール内の他のセルに影響を与えません。
  * グリッド上のどこに書き込まれた値は、次のルールのシーケンス、または残りのルールがない場合は次のタイムステップで利用可能です。
  * `add!`や`sub!`のような原子演算子が常にグリッドへの書き込みに使用される場合、レースコンディションはどのハードウェアでも発生しません。
