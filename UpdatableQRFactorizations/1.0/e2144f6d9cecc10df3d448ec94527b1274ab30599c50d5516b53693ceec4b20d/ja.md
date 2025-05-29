```
    add_column!(F::UpdatableGivensQR, x::AbstractVector, k::Int = size(F, 2) + 1)
```

既存のQR因子分解 `F` がある行列に対して、新しい列 `x` を `k`ᵗʰ 列として追加した後の同じ行列の因子分解を計算します。計算の複雑さ: O(nm) ただし size(F) = (n, m)。警告: 既存の因子分解を上書きします。
