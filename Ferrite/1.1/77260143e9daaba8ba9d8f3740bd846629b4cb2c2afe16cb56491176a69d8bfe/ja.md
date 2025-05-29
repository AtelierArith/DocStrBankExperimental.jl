```
DofHandler(grid::Grid)
```

グリッド `grid` に基づいて `DofHandler` を構築します。

構築後、任意の数の離散フィールドを [`add!`](@ref) を使用して DofHandler に追加できます。構築は [`close!`](@ref) を呼び出すことで完了します。

デフォルトでは、フィールドはグリッドのすべての要素に追加されます。グリッドのサブドメインにフィールドを制限するには、[`SubDofHandler`](@ref) を参照してください。

# 例

```julia
dh = DofHandler(grid)
ip_u = Lagrange{RefTriangle, 2}()^2 # フィールド u のためのベクトル補間
ip_p = Lagrange{RefTriangle, 1}()   # フィールド p のためのスカラー補間
add!(dh, :u, ip_u)
add!(dh, :p, ip_p)
close!(dh)
```

!!! note "自由度の番号付け"
    自由度の番号付けは、関連するグリッドのノードのグローバル番号付けに従わないことに注意してください。

