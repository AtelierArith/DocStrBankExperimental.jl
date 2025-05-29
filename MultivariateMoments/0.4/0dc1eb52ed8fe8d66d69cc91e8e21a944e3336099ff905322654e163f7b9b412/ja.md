```
struct Echelon{D,S<:Union{Nothing,SemialgebraicSets.AbstractAlgebraicSolver}} <:
    MacaulayNullspaceSolver
    solver::S
end
```

与えられた [`MacaulayNullspace`](@ref) は、そのエchelon形式を計算します（*Canonical Null Space* に対応する [D13]）ガウス消去法を用いて。このエchelon形式から、左のヌル空間は [HL05, (8)] を使用して簡単に計算できます。この左のヌル空間は、多項式方程式の系を形成します。

!!! note
    [`compute_support!`](@ref) の文脈において、[`MacaulayNullspace`](@ref) が [`SVDLDLT`](@ref) を使用して得られた場合、左のヌル空間は削除された無視できる特異値に対応する特異ベクトルから簡単に得られます。しかし、[LLR08, Section 4.4.5] で述べられているように、これらは通常、過剰決定基底を与えます。[S04, Section 10.8.2] で示されているように、数値的理由から過剰決定基底を避けることが望ましいです。このため、この方法は重要な特異値のエchelon形式から左のヌル空間を計算します。


`B` をこのエchelon形式のピボットの行に対応する単項式の集合とします。モーメント行列が [L09, Section 5.3] で説明されている*フラット拡張*特性を満たす場合、`B` の*境界*のすべての単項式（[LLR08, (2.3)] で定義される）は、行列の行に対応します。その場合、[HL05, (8)] によって得られた系の多項式は、`B` の*書き換えファミリー*を形成します [L09, (2.16)] いわゆる `B`*-境界前基底*（[LLR08, (2.4)] で定義される）。したがって、これらは乗法行列を計算するために使用できます。

[HL05] Henrion, D. & Lasserre, J-B. *Detecting Global Optimality and Extracting Solutions of GloptiPoly* 2005

[D13] Dreesen, Philippe. *Back to the Roots: Polynomial System Solving Using Linear Algebra* Ph.D. thesis (2013)

[L09] Laurent, Monique. *Sums of squares, moment matrices and optimization over polynomials.* Emerging applications of algebraic geometry (2009): 157-270.

[LLR08] Lasserre, Jean Bernard and Laurent, Monique, and Rostalski, Philipp. *Semidefinite characterization and computation of zero-dimensional real radical ideals.* Foundations of Computational Mathematics 8 (2008): 607-647.

[S04] Stetter, Hans J. *Numerical polynomial algebra.* Society for Industrial and Applied Mathematics, 2004.
