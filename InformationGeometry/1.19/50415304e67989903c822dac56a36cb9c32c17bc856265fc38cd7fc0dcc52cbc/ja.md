`HyperCube`型は、$N$個の実数区間のデカルト積の形で直方体領域を指定するために使用され、関数間の積分やプロットのためのドメインを渡す便利な方法を提供します。`HyperCube`オブジェクト`cube`型には、実数区間の下限と上限の境界をそれぞれ格納する2つのベクトル`cube.L`と`cube.U`という2つのフィールドがあります。`HyperCube`を構築するための例：

```julia
HyperCube([[1,3],[π,2π],[-500,100]])
HyperCube([1,π,-500],[3,2π,100])
HyperCube([[-1,1]])
HyperCube([-1,1])
HyperCube(collect([-7,7.] for i in 1:3))
```

`HyperCube`オブジェクト`X`から計算できる量や操作の例：

```julia
CubeVol(X)
TranslateCube(X,v::AbstractVector)
CubeWidths(X)
```
