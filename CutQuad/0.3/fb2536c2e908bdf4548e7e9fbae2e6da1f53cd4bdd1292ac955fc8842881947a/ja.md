```
surf_wts, surf_pts = 
    cut_surf_quad(cell, phi, num_quad [, fit_degree=num_quad-1])
```

`phi(x)=0` で定義された表面の表面積分を返します。これは、`cell` のハイパーレクタングル上で、`phi` はレベルセット関数です。例えば、表面が `cell` の側面のいずれかに平行な平面である場合、`num_quad^(Dim-1)` 点の合計を持つテンソル積ガウス・レジェンドル積分が得られます。ここで、`Dim` は領域の次元です。`fit_degree` パラメータは、アルゴリズムライブラリがレベルセット関数 `phi` を表現するために使用するバーンスタイン多項式の次数を示します。

# 例

```julia-repl
julia> using CutQuad, RegionTrees

julia> using StaticArrays: SVector

julia> phi = x-> 4*(x[1] + 1)^2 + 36*(x[2] - 0.5)^2 - 9;

julia> cell = HyperRectangle(SVector{2}([0.0; 0.0]), SVector{2}([1.0; 1.0]));

julia> surf_wts, surf_pts = cut_surf_quad(cell, phi, 3, fit_degree=2)
```
