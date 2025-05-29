`dummycreate`は、グループのベクトルからゼロと一の行列を作成することを可能にします。入力引数`inputmat`は`Vector`でなければなりません。

# 例

```julia-repl
julia> dummycreate([1.0, 2.0])

2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

dummycreate(['a', 'b'])

2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

dummycreate([1, 'a', 'b', 1])

4×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
 1.0  0.0  0.0
```
