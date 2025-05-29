```
StudentCopula
```

t-スチューデントコピュラ

フィールド

  * Σ::Matrix{Real} - 相関行列は対称で、正定値であり、対角に1が必要です
  * ν::Int - 自由度のパラメータ n.o. が必要で ν > 0

コンストラクタ:

```
StudentCopula(Σ::Matrix{Real}, ν::Int)
```

```jldoctest

julia> StudentCopula([1. 0.5; 0.5 1.], 4)
StudentCopula([1.0 0.5; 0.5 1.0], 4)

```
