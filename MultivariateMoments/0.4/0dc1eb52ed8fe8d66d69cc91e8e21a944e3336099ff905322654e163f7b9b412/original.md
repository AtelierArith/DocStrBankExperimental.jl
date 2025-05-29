```
struct Echelon{D,S<:Union{Nothing,SemialgebraicSets.AbstractAlgebraicSolver}} <:
    MacaulayNullspaceSolver
    solver::S
end
```

Given a [`MacaulayNullspace`](@ref), computes its echelon form (corresponding to the *Canonical Null Space* of [D13]) with Gaussian elimination. From this echelon form, the left null space can easily be computed using using [HL05, (8)]. This left null space forms a system of polynomial equations.

!!! note
    In the context of [`compute_support!`](@ref), if the [`MacaulayNullspace`](@ref) was obtained using [`SVDLDLT`](@ref), the left null space can easily be obtained from the singular vectors corresponding to the negligeable singular values that were removed. However, as mentioned [LLR08, Section 4.4.5], these will usually give an overdetermined bases. As shown in [S04, Section 10.8.2], it is desirable to avoid overdetermined bases because it could lead to inconsistencies in the basis for numerical reasons. For this reason, this method computes the left null space from the echelon form of the significant singular values instead.


Let `B` be the set of monomials corresponding to the rows of the pivots of this echelon form.  If the moment matrix satisfies the *flat extension* property described in [L09, Section 5.3] then all monomials of the *border* of `B` (as defined in [LLR08, (2.3)]) will correspond to a row of of the matrix. In that case, the polynomial of the system obtained by [HL05, (8)] form a *rewriting family* for `B` [L09, (2.16)] a.k.a. a `B`*-border prebasis* (as defined in [LLR08, (2.4)]). Therefore, they can be used to compute multiplication matrices.

[HL05] Henrion, D. & Lasserre, J-B. *Detecting Global Optimality and Extracting Solutions of GloptiPoly* 2005

[D13] Dreesen, Philippe. *Back to the Roots: Polynomial System Solving Using Linear Algebra* Ph.D. thesis (2013)

[L09] Laurent, Monique. *Sums of squares, moment matrices and optimization over polynomials.* Emerging applications of algebraic geometry (2009): 157-270.

[LLR08] Lasserre, Jean Bernard and Laurent, Monique, and Rostalski, Philipp. *Semidefinite characterization and computation of zero-dimensional real radical ideals.* Foundations of Computational Mathematics 8 (2008): 607-647.

[S04] Stetter, Hans J. *Numerical polynomial algebra.* Society for Industrial and Applied Mathematics, 2004.
