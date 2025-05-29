```
DispersedField(f::DispersedField, de)
```

すでに分散されたフィールド `f` に別の [`DispersiveElement`](@ref) `de` をスタッキングすることは、転送関数を掛け合わせることで実現され、最も早く適用されたものが最も右側の因子として扱われます：

$$
H(\omega) = H_n(\omega) ... H_3(\omega)H_2(\omega)H_1(\omega).
$$
