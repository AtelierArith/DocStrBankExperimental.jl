```
wts, pts = cut_face_quad(face, dir, phi, num_quad [, fit_degree=num_quad-1])
```

`face`で定義されたハイパーレクタングルとレベルセット関数`phi`のための数値積分を返します。面は単位法線を持ち、その唯一の非ゼロ成分は方向`dir`にあります。さらに、空間次元が`Dim`である場合（これは`face`のパラメータによって決定されます）、ハイパーレクタングルは方向`dir`において幅がゼロである必要があります。カットされていない面（すなわち、`phi(x) > 0`が`face`上のすべての`x`に対して成り立つ）における標準的な数値積分は、`num_quad^(Dim-1)`点の合計を持つテンソル積ガウス・レジェンドル数値積分を使用します。`fit_degree`パラメータは、アルゴリズムライブラリがレベルセット関数`phi`を表現するために使用するバーンスタイン多項式の次数を示します。

# 例

```julia-repl
julia> using CutQuad, RegionTrees

julia> using StaticArrays: SVector

julia> phi = x-> 4*(x[1] + 1)^2 + 36*(x[2] - 0.5)^2 - 9;

julia> face = HyperRectangle(SVector{2}([0.0; 0.0]), SVector{2}([0.0; 1.0]));

julia> face_wts, face_pts = cut_face_quad(face, 1, phi, 3, fit_degree=2)
```
