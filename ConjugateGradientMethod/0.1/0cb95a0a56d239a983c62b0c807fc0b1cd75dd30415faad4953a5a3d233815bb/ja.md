```
cg(A, b, [iterpart=1.0])
cg(A, b, [iternum=size(A,1)])
```

共役勾配法を使用して最小二乗問題 $\min\|Ax - b\|^2$ を解きます。初期値を使用するには `cg!` を参照してください。

`iternum` は停止するまでの反復回数を指定します（最小1）。 `iterpart` = `iternum` / $size(A,1)$

## 例

```julia-repl
julia> cg([1 2; 3 4], [1, 2])
2-element Array{Float64,1}:
5.551115123125783e-17
0.5000000000000012
```

他に [`cg!`](@ref) と [`@cg`](@ref) を参照してください。
