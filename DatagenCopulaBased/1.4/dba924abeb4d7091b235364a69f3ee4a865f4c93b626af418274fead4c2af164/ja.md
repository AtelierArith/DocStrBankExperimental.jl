```
ガウスコピュラ
```

ガウスコピュラ

フィールド:

  * Σ - 相関行列は対称で、正定値であり、対角に1がある必要があります

コンストラクタ

```
GaussianCopula(Σ::Matrix{T}) where T <: Real
```

```jldoctest

julia> GaussianCopula([1. 0.5; 0.5 1.])
GaussianCopula([1.0 0.5; 0.5 1.0])

```
