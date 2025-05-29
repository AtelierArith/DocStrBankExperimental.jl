```
SubDofHandler(dh::AbstractDofHandler, cellset::AbstractVecOrSet{Int})
```

親の `dh` から `cellset` に関連する `sdh::SubDofHandler` を作成します。これにより、ドメインの一部にフィールドを追加したり、異なる補間やセルタイプ（例：`Triangles` と `Quadrilaterals`）を使用したりできます。すべてのフィールドとセルタイプは、1 つの `SubDofHandler` 内で同じでなければなりません。

構築後、任意の数の離散フィールドを [`add!`](@ref) を使用して SubDofHandler に追加できます。構築は、親の `dh` に対して [`close!`](@ref) を呼び出すことで完了します。

# 例

"Triangle" と "Quadrilateral" セルを含む `grid` があり、これらのセルに対して "triangles" と "quadilaterals" のセルセットがあると仮定します。

```julia
dh = DofHandler(grid)

sdh_tri = SubDofHandler(dh, getcellset(grid, "triangles"))
ip_tri = Lagrange{RefTriangle, 2}()^2 # フィールド u のためのベクトル補間
add!(sdh_tri, :u, ip_tri)

sdh_quad = SubDofHandler(dh, getcellset(grid, "quadilaterals"))
ip_quad = Lagrange{RefQuadrilateral, 2}()^2 # フィールド u のためのベクトル補間
add!(sdh_quad, :u, ip_quad)

close!(dh) # 親を閉じて完了
```
