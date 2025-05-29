```
symmetric(A, Q::QDHT)
```

サンプル `A` から対称配列を作成します。軸上のサンプルも含まれます。

`A` が `[r₁, r₂, r₃, ...]` でサンプリングされている場合、`[...-r₃, -r₂, -r₁, 0, r₁, r₂, r₃...]` でサンプリングされた配列を生成します。

# 例

```jldoctest
julia> q = QDHT{0, 1}(10, 128); A = exp.(-q.r.^2);
julia> As = symmetric(A, q);
julia> size(As)
(257,)
julia> As[1:128] == A[128:-1:1]
true
julia> As[129] ≈ 1 # should be exp(0) = 1
true
julia> As[130:end] == A
true
```
