```
project(proj::L2Projector, vals, [qr_rhs::QuadratureRule])
```

データ `vals` をグリッドのノードに対してプロジェクター `proj` を使用して L2 プロジェクションを行います（[`L2Projector`](@ref) を参照）。

`project` は右辺を積分し、次のプロジェクション方程式からプロジェクション $u$ を解きます：プロジェクション $u \in U_h(\Omega) \subset L_2(\Omega)$ を見つけることが必要です。すなわち、

$$
\int v u \ \mathrm{d}\Omega = \int v f \ \mathrm{d}\Omega \quad \forall v \in U_h(\Omega),
$$

ここで $f \in L_2(\Omega)$ はプロジェクトするデータです。関数空間 $U_h(\Omega)$ は `proj` における補間によって与えられる有限要素近似です。

データ `vals` はセル番号でインデックス付けされた `AbstractVector` または `AbstractDict` である必要があります。`vals` の各インデックスは、各セルのガウス点に対して1つの要素を持つ `AbstractVector` を返す必要があります。

`proj` が `L2Projector(ip, grid, set)` を呼び出すことで作成された場合、`qr_rhs` を指定する必要があります。そうでない場合、`add!(proj, args...)` を呼び出す際に各ドメインに対してこれが追加されます。

また、`vals` は行列であり、列インデックスがセル番号を参照し、行インデックスがガウス点番号に対応することもできます。例（スカラー）入力データ：

```julia
vals = [
    [0.44, 0.98, 0.32], # 要素 1 のガウス点 1, 2, 3 のデータ
    [0.29, 0.48, 0.55], # 要素 2 のガウス点 1, 2, 3 のデータ
    # ...
]
```

または行列形式で同等：

```julia
vals = [
    0.44 0.29 # ...
    0.98 0.48 # ...
    0.32 0.55 # ...
]
```

プロジェクト可能なデータ型は `Number` と `AbstractTensor` です。

!!! note
    返されるデータの順序は `L2Projector` の内部 `DofHandler` の順序に対応しています。データはさらに [`evaluate_at_points`](@ref) および [`evaluate_at_grid_nodes`](@ref) で分析できます。結果をエクスポートするには [`write_projection`](@ref) を使用してください。


```
