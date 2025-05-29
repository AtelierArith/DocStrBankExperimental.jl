```
wts, pts = cut_cell_quad(cell, phi, num_quad [, fit_degree=num_quad-1])
```

`cell` で定義された領域とレベルセット関数 `phi` に対する体積の数値積分を返します。非カット領域（すなわち、すべての `x` に対して `phi(x) > 0`）における標準的な数値積分は、`num_quad^Dim` 点の合計を持つテンソル積ガウス・レジェンドル数値積分を使用します。ここで、`Dim` は領域の次元です。`fit_degree` パラメータは、アルゴリズムライブラリがレベルセット関数 `phi` を表現するために使用するバーンスタイン多項式の次数を示します。

# 例

```julia-repl
julia> using CutQuad, RegionTrees

julia> using StaticArrays: SVector

julia> phi = x-> 4*(x[1] + 1)^2 + 36*(x[2] - 0.5)^2 - 9;

julia> cell = HyperRectangle(SVector{2}([0.0; 0.0]), SVector{2}([1.0; 1.0]));

julia> wts, pts = cut_cell_quad(cell, phi, 3, fit_degree=2)
```
