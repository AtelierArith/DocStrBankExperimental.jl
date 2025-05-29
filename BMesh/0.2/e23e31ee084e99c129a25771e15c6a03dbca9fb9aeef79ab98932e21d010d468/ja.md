8ノードソリッド要素の3D背景メッシュを生成します (:solid3D)

```
Bmesh_solid_3D(Lx::Float64,nx::Int64,Ly::Float64,ny::Int64,Lz::Float64,nz::Int64)
```

ここで

```
Lx  = X方向の長さ（横方向）
nx  = X方向の分割数（要素数）
Ly  = Y方向の長さ（横方向）
ny  = Y方向の分割数（要素数）
Lz  = Z方向の長さ（垂直方向）
nz  = Z方向の分割数（要素数）
```

は次を返します

```
Bmesh3D(:solid3D,nn,ne,coord,connect,Lx,Ly,Lz,nx,ny,nz)
```

ここで

```
nn      = ノードの数 
ne      = 要素の数
coord   = ノード座標 (x y z) の nn x 3 行列 
connect = 接続性を持つ ne x 8 行列。
```

ノードはz=0からz=Lzまで、平面ごとに生成されます。接続性も同様のパターンに従います。
