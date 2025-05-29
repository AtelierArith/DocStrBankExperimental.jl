```
generate_sites(lattice::AbstractLattice{D}, repeats::Vararg{Int,D}; scale=1.0)
```

指定された `lattice` をタイル状に配置することで [`AtomList`](@ref) インスタンスを返します。タイルは、最初の次元に沿って `m` 回、2 番目の次元に沿って `n` 回、その他の次元に沿って繰り返されます。`scale` は、格子定数と原子の位置を再スケールする実数です。
