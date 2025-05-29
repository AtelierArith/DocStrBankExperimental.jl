```
infinite_place(e::NumFieldEmb)
```

与えられた複素埋め込みによって誘導される無限位を構築します。

```jldoctest
julia> K,  = quadratic_field(5);

julia> infinite_place(complex_embedding(K, 2.24))
無限位
実数二次体 x^2 - 5 によって定義され
K の 2.24 に対応する複素埋め込みに対応します
```
