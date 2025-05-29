```
struct FlatExtension{
    MMS<:SemialgebraicSets.AbstractMultiplicationMatricesSolver,
}
    multiplication_matrices_solver::MMS
end
```

Given a moment matrix satisfying the *flat extension* property described in [L09, Section 5.3], computes the multiplication matrices using the formula given in [L09, Lemma 6.21] or [LLR08, Section 4.4.4]. Given the multiplication matrices, the solutions are obtained with `multiplication_matrices_solver`.

[L09] Laurent, Monique. *Sums of squares, moment matrices and optimization over polynomials.* Emerging applications of algebraic geometry (2009): 157-270.

[LLR08] Lasserre, Jean Bernard and Laurent, Monique, and Rostalski, Philipp. *Semidefinite characterization and computation of zero-dimensional real radical ideals.* Foundations of Computational Mathematics 8 (2008): 607-647.
