```
almExplicitIndex(lmax) -> Vector{Int}
almExplicitIndex(lmax, mmax) -> Vector{Int}
almExplicitIndex(alm::Alm{T}) where {T} -> Vector{Int}
```

明示的インデックススキームを計算します。すなわち、$\mathrm{index} = \ell^2 + \ell + m + 1$ を特定の $ℓ$ と $m$ まで計算します（指定されている場合）または渡された `Alm` から取得します。渡されない場合、`mmax` は `lmax` にデフォルト設定されます。`lmax` と `mmax` が矛盾しているか負の値の場合、`DomainError` 例外がスローされます。
