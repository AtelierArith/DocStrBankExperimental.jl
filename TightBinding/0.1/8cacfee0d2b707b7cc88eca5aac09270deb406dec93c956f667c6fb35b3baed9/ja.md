```
set_Lattice(dim::Integer,vectors::Array{Array{Float64,1},1})
```

格子を初期化します。ハミルトニアンを作成する前にこれを呼び出す必要があります。dim: システムの次元。vector:: 基本ベクトル。

例:

1次元システム

```julia
la1 = set_Lattice(1,[[1.0]])
```

2次元システム

```julia
a1 = [sqrt(3)/2,1/2]
a2 = [0,1]
la2 = set_Lattice(2,[a1,a2])
```

3次元システム

```julia
a1 = [1,0,0]
a2 = [0,1,0]
a3 = [0,0,1]
la2 = set_Lattice(3,[a1,a2,a3])
```
