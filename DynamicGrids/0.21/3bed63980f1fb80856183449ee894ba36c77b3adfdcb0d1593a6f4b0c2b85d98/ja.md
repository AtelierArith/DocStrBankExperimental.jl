```
Neighbors <: NeighborhoodRule

Neighbors(f, neighborhood=Moor(1))
Neighbors{R,W}(f, neighborhood=Moore())
```

[`NeighborhoodRule`](@ref) は、最初の `R` グリッドに対して [`Neighborhood`](@ref) オブジェクトを受け取り、その後に必要なグリッドのセル値を受け取ります。これは [`Cell`](@ref) と同様です。

返される値は `W` グリッドに書き込まれます。

すべての [`NeighborhoodRule`](@ref) と同様に、グリッドの端での境界チェックを行う必要はありません。これは内部で処理されます。

特定の値（しばしばゼロ）が一般的であり、安全に無視できる場合、[`SparseOpt`](@ref) を使用することで近傍のパフォーマンスが向上する可能性があります。

## 例

グリッド `:a` でライフゲームのグライダーを実行します：

```jldoctest
using DynamicGrids
const sum_states = (0, 0, 1, 0, 0, 0, 0, 0, 0), 
                   (0, 0, 1, 1, 0, 0, 0, 0, 0)
life = Neighbors{:a}(Moore(1)) do data, hood, a, I
    sum_states[a + 1][sum(hood) + 1]
end
init = Bool[
     0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
     0 0 0 0 0 1 1 1 0 0 0 0 0 0 0
     0 0 0 0 0 0 0 1 0 0 0 0 0 0 0
     0 0 0 0 0 0 1 0 0 0 0 0 0 0 0
     0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
]
output = REPLOutput((; a=init); fps=25, tspan=1:50)
sim!(output, Life{:a}(); boundary=Wrap())
output[end][:a]

# output
5×15 Matrix{Bool}:
 0  0  1  0  1  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  1  1  0  0  0  0  0  0  0  0  0  0

```
