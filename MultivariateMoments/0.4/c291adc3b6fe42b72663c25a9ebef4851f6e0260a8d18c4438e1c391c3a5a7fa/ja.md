```
struct BorderBasis{D,T,MT<:AbstractMatrix{T},B}
    dependence::BasisDependence{D,B}
    matrix::MT
end
```

この行列は、`standard` にインデックス付けされた行と `border` にインデックス付けされた列を持ち、理想 `border .- matrix' * standard` の `standard`-border 基底です [LLR08, Section 2.5]。これを乗算行列ソルバーで解くためには、基底 `border` が `standard` の *corners* の集合のスーパーセットである必要があり、`standard` の *border* であることが十分です。

[LLR08] Lasserre, Jean Bernard and Laurent, Monique, and Rostalski, Philipp. *Semidefinite characterization and computation of zero-dimensional real radical ideals.* Foundations of Computational Mathematics 8 (2008): 607-647.
