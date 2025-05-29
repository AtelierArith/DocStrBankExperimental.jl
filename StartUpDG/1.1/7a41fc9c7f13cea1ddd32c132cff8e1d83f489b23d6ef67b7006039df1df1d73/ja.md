```
uniform_mesh(elem::Line,Kx)
uniform_mesh(elem::Tri,Kx,Ky)
uniform_mesh(elem::Quad,Kx,Ky)
uniform_mesh(elem::Hex,Kx,Ky,Kz)
uniform_mesh(elem, K)
```

一様な `Kx`（`Ky`、`Kz` による）メッシュは $[-1,1]^d$ 上にあり、ここで `d` は空間次元です。`(VX,VY,VZ)`、`EToV` を返します。`K` が1つだけ指定されている場合、各座標方向に `K` 要素を持つ一様メッシュであると仮定します。

`K` はキーワード引数 `K1D` を使用して指定することもでき、例えば `uniform_mesh(elem; K1D = 16)` のようにします。
