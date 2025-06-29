```
pairwiseidentical(data::PopData)
```

すべての個体のペア間で各ローカスにおける同一の遺伝子型の割合のペアワイズ行列を返します。

### 例:

```
julia> cats = @nancycats ;

julia> pairwiseidentical(cats)
237×237 Named Matrix{Float64}
A ╲ B │     N215      N216  …      N289      N290
──────┼──────────────────────────────────────────
N215  │      1.0       0.5  …  0.142857  0.166667
N216  │      0.5       1.0     0.142857  0.166667
N217  │     0.25     0.125        0.125  0.142857
N218  │    0.375      0.25         0.25  0.142857
N219  │    0.375     0.375         0.25  0.142857
⋮              ⋮         ⋮  ⋱         ⋮         ⋮
N296  │      0.5  0.333333          0.0       0.0
N297  │ 0.166667  0.166667     0.428571  0.285714
N281  │ 0.142857  0.142857         0.25  0.428571
N289  │ 0.142857  0.142857          1.0  0.142857
N290  │ 0.166667  0.166667  …  0.142857       1.0
```
