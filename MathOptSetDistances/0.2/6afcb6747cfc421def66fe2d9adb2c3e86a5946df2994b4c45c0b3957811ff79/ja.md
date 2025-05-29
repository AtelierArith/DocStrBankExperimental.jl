```
projection_gradient_on_set(::DefaultDistance, v::AbstractVector{T}, sets::AbstractVector{<:MOI.AbstractSet})
```

ベクトル `v` の `sets` の積の射影の導関数*projection*gradient*on*set[i,j] = ∂projection*on*set[i] / ∂v[j] ここで `projection*on_set` は `v` の `cone` に対する射影を示します。

コーンに対する射影とその導関数の表現については、こちらを参照してください: https://stanford.edu/~boyd/papers/pdf/cone*prog*refine.pdf
