```
L2Projector(grid::AbstractGrid)
```

`L2Projector`を初期化して、関数空間に対して数値積分データを射影します。関数空間を定義するには、`close!`する前に`add!`を使って異なるセルセットの補間を追加します。以下の例を参照してください。

`L2Projector`は射影方程式の統合された左辺として機能します：射影 $u \in U_h(\Omega) \subset L_2(\Omega)$ を見つけることが求められます。

$$
\int v u \ \mathrm{d}\Omega = \int v f \ \mathrm{d}\Omega \quad \forall v \in U_h(\Omega),
$$

ここで、$f \in L_2(\Omega)$ は射影するデータです。関数空間 $U_h(\Omega)$ は、`L2Projector`に`add!`された補間によって与えられる有限要素近似です。

### 例

```julia
proj = L2Projector(grid)
qr_quad = QuadratureRule{RefQuadrilateral}(2)
add!(proj, quad_set, Lagrange{RefQuadrilateral, 1}(); qr_rhs = qr_quad)
qr_tria = QuadratureRule{RefTriangle}(1)
add!(proj, tria_set, Lagrange{RefTriangle, 1}(); qr_rhs = qr_tria)
close!(proj)

vals = Dict{Int, Vector{Float64}}() # Vector{Vector}でも可、
                                    # cellnrでインデックス付け
for (set, qr) in ((quad_set, qr_quad), (tria_set, qr_tria))
    nqp = getnquadpoints(qr)
    for cellnr in set
        vals[cellnr] = rand(nqp)
    end
end

projected = project(proj, vals)
```

ここで、`projected`は例えば[`PointEvalHandler`](@ref)や[`evaluate_at_grid_nodes`](@ref)とともに使用できます。
