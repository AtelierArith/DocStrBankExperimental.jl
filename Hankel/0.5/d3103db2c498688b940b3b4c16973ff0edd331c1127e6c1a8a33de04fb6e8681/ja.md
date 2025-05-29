```
integrateR(A, Q::QDHT; dim=1)
```

実空間における `Q` の開口部に対する `A` の放射積分。

`A` がサンプル点 `Q.r` における関数 `f(r)` のサンプルを含むと仮定すると、`integrateR(A, Q)` は r=0 から r=∞ までの ∫f(r)r dr を近似します。

!!! note
    `integrateR` と `integrateK` はパースバルの定理を満たします。すなわち、ある配列 `A` に対して、`integrateR(abs2.(A), q)` と `integrateK(abs2.(q*A), q)` は等しいですが、**しかし** `integrateR(A, q)` と `integrateK(q*A, q)` は **等しくありません**。


!!! warning
    関数を積分するために `integrateR` を使用すること（すなわち `A` ではなく `abs2(A)`）は、0次の QDHT のみサポートされています。詳細については [Derivations](@ref) を参照してください。


# 例

```jldoctest
julia> q = QDHT{0, 1}(10, 128); A = exp.(-q.r.^2/2);
julia> integrateR(abs2.(A), q) ≈ 0.5 # ∫exp(-r²)r dr の解析解は 0 から ∞ まで
true
```
