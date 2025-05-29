```
struct FlatExtension{
    MMS<:SemialgebraicSets.AbstractMultiplicationMatricesSolver,
}
    multiplication_matrices_solver::MMS
end
```

与えられたモーメント行列が[L09, Section 5.3]で説明されている*フラット拡張*の性質を満たす場合、[L09, Lemma 6.21]または[LLR08, Section 4.4.4]で与えられた式を使用して乗法行列を計算します。乗法行列が与えられると、`multiplication_matrices_solver`を使用して解を得ることができます。

[L09] Laurent, Monique. *Sums of squares, moment matrices and optimization over polynomials.* Emerging applications of algebraic geometry (2009): 157-270.

[LLR08] Lasserre, Jean Bernard and Laurent, Monique, and Rostalski, Philipp. *Semidefinite characterization and computation of zero-dimensional real radical ideals.* Foundations of Computational Mathematics 8 (2008): 607-647.
