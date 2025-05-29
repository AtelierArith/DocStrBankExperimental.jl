```
changebasis(P::AbstractFunctionSpace, P′::AbstractFunctionSpace)
```

$$
P ⊆ P′
$$

の場合は `changebasis_R(P, P′)` を返します。それ以外の場合は $P ⊑ P′$ の場合に `changebasis_R(P, P′)` を返します。$P ⊈ P′$ かつ $P ⋢ P′$ の場合はエラーをスローします。
