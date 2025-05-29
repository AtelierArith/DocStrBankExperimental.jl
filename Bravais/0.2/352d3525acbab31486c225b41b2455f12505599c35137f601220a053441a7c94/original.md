```
nigglibasis(Rs; rtol=1e-5, max_iterations=200)
```

Given a set of primitive basis vectors `Rs`, return a basis `Rs′` for the corresponding Niggli-reduced unit cell, as well as a transformation matrix `P`, such that `Rs′ = transform(Rs, P)` (see [`transform`](@ref)).

## Definition

A Niggli-reduced basis $(\mathbf{a}, \mathbf{b}, \mathbf{c})$ represents a unique choice of basis for any given lattice (or, more precisely, a unique choice of the basis vector lengths $|\mathbf{a}|, |\mathbf{b}|, |\mathbf{c}|$, and mutual angles between  $\mathbf{a}, \mathbf{b}, \mathbf{c}$). This uniqueness is one of the main motivations for computing the Niggli reduction procedure, as it enables easy comparison of lattices. Additionally, the associated Niggli-reduced basis vectors $(\mathbf{a}, \mathbf{b}, \mathbf{c})$, fulfil several conditions [^3]:

1. **"Main" conditions:**

      * The basis vectors are sorted by increasing length: $|\mathbf{a}| ≤ |\mathbf{b}| ≤ |\mathbf{c}|$.
      * The angles between basis vectors are either all acute or all non-acute.
2. **"Special" conditions:**

      * Several special conditions, applied in "special" cases, such as $|\mathbf{a}| = |\mathbf{b}|$ or  `\mathbf{b}\cdot\mathbf{c} = \tfrac{1}{2}|\mathbf{b}|^2`. See Ref. [^3] for details.

Equivalently, the Niggli-reduced basis fulfils the following geometric conditions (Section 9.3.1 of Ref. [^3]):

  * The basis vectors are sorted by increasing length.
  * The basis vectors have least possible total length, i.e., ``|\mathbf{a}| + |\mathbf{b}|

      * |\mathbf{c}|`` is minimum. I.e., the associated Niggli cell is a Buerger cell.
  * The associated Buerger cell has maximum deviation among all other Buerger cells, i.e., the basis vector angles $α, β, γ$ maximize $|90° - α| + |90° - β| + |90° - γ|$.

## Keyword arguments

  * `rtol :: Real`: relative tolerance used in the Grosse-Kunstleve approach for floating point comparisons (default: `1e-5`).
  * `max_iterations :: Int`: maximum number of iterations in which to cycle the Krivy-Gruber steps (default: `200`).

## Implementation

Implementation follows the algorithm originally described by Krivy & Gruber [^1], with the stability modificiations proposed by Grosse-Kunstleve et al. [^2] (without which the  algorithm proposed in [^1] simply does not work on floating point hardware).

[^1] I. Krivy & B. Gruber. A unified algorithm for determinign the reduced (Niggli) cell,     [Acta Crystallogr. A **32**, 297 (1976)](https://doi.org/10.1107/S0567739476000636). [^2] R.W. Grosse-Kunstleve, N.K. Sauter, & P.D. Adams, Numerically stable algorithms for the     computation of reduced unit cells,     [Acta Crystallogr. A **60**, 1 (2004)](https://doi.org/10.1107/S010876730302186X) [^3] Sections 9.2 & 9.3, International Tables of Crystallography, Volume A, 5th ed. (2005).
