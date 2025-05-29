2D背景メッシュを生成するための4ノードソリッド（平面）要素（:solid2D）

```
Bmesh_solid_2D(Lx::Float64, nx::Int64, Ly::Float64, ny::Int64)
```

ここで

```
Lx  = X方向の長さ（水平方向）
nx  = X方向の分割数（要素数）
Ly  = Y方向の長さ（垂直方向）
ny  = Y方向の分割数（要素数）
```

は次のものを返します

```
Bmesh2D(:solid2D,nn,ne,coord,connect,Lx,Ly, nx,ny)
```

ここで

```
nn      = ノードの数 
ne      = 要素の数
coord   = ノード座標（x y）を持つnn x 2の行列 
connect = 接続性を持つne x 4の行列
```
