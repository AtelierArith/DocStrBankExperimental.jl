```
integrateK(Ak, Q::QDHT; dim=1)
```

Qの開口部における`A`の放射状積分、逆空間で。

`A`がサンプル点`Q.k`での関数`f(k)`のサンプルを含むと仮定すると、`integrateR(A, Q)`は∫f(k)k dkをk=0からk=∞まで近似します。

!!! note
    `integrateR`と`integrateK`はパースバルの定理を満たします。すなわち、ある配列`A`に対して、`integrateR(abs2.(A), q)`と`integrateK(abs2.(q*A), q)`は等しいですが、**しかし** `integrateR(A, q)`と`integrateK(q*A, q)`は**等しくありません**。


# 例

```jldoctest
julia> q = QDHT{0, 1}(10, 128); A = exp.(-q.r.^2/2);
julia> integrateR(abs2.(A), q) ≈ 0.5 # ∫exp(-r²)r drの解析解は0から∞まで
true
julia> Ak = q*A;
julia> integrateK(abs2.(Ak), q) ≈ 0.5 # 同じ結果
true

```
