```
cg!(x, A, b, [iterpart=1.0])
cg!(x, A, b, [iternum=size(A,1)])
```

最小二乗問題 $\min\|Ax - b\|^2$ を共役勾配法を使用して解きます。`x` は初期値として使用され、結果で置き換えられます。

`iternum` は停止するまでの反復回数を指定します（最小1）。

## 例

```julia-repl
julia> x = zeros(2);

julia> cg!(x, [1 2; 3 4], [1, 2])
2-element Array{Float64,1}:
5.551115123125783e-17
0.5000000000000012
```

関連情報は [`cg`](@ref) と [`@cg`](@ref) を参照してください。
