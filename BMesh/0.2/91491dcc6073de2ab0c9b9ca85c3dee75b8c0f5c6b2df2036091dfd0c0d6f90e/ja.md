3D背景メッシュを生成するためのトラス:3D要素

```
Bmesh_truss_3D(Lx::Float64,nx::Int64,Ly::Float64,ny::Int64,Lz::Float64,nz::Int64)
```

ここで

```
Lx  = X方向の長さ（水平方向）
nx  = X方向の分割数（要素数）
Ly  = Y方向の長さ（水平方向）
ny  = Y方向の分割数（要素数）
Lz  = Z方向の長さ（垂直方向）
nz  = Z方向の分割数（要素数）
```

は次を返します

```
Bmesh3D(:truss3D,nn,ne,coord,connect,Lx,Ly,Lz,nx,ny,nz)
```

ここで

```
nn      = ノードの数 
ne      = 要素の数
coord   = ノード座標（x y z）を持つnn x 3の行列 
connect = 接続性を持つne x 2の行列。
```

ノードはz=0からz=Lzまで、平面ごとに生成されます。接続性も同様のパターンに従います。
