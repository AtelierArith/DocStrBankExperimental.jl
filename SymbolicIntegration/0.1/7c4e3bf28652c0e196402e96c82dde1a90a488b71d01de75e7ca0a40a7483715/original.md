```
TowerOfDifferentialFields(Hs) -> K, gs, D
```

Construct tower of differential fields.

Given `Hs = [H₁,...,Hₙ]` with `Hᵢ` in `C(x,t₁,...,tₙ)` (i.e., they are fractions of multivariate polynomials in variables `x, t₁,...,tₙ` over a field `C`)  such that `Hᵢ` can be represented as a polynomial in `tᵢ` with coefficients  in `C(x, t₁,...,tᵢ₋₁)` (in particular, `Hᵢ` does not depend on `tᵢ₊₁,...,tₙ`), return a field `K = C(x)(t₁)...(tₙ)` isomorphic to `C(x, t₁,...,tₙ)` and a derivation `D` on `K` such that `K` is constructed by iteratively adjoining the indeterminates `x`, `t₁`,...,`tₙ`, `C` is the constant field of `D`, `D` is `d/dx` on `C(x)`, and `D` is iteratively extended from `C(x)(t₁)...(tᵢ₋₁)` to `C(x)(t₁)...(tᵢ)` such that `tᵢ` is monomial over `C(x)(t₁)...(tᵢ₋₁)` with `D(tᵢ)=Hᵢ=Hᵢ(x, t₁,....,tᵢ)`. The generators `x` of C(x) over C and `tᵢ` of `C(x)(t₁)...(tᵢ)` over `C(x)(t₁)...(tᵢ₋₁)` are returned as `gs=[x, t₁,...,tₙ]`. (Note that these generators, although here denoted by the same symbols for simplicity, are isomorphic but not identical to  the generators `x, t₁,...,tₙ` of `C(x,t₁,...,tₙ)` given implicitely as the variables of the rational functions `Hᵢ`.)

# Example

```julia
R, (x, t1, t2) = PolynomialRing(QQ, [:x, :t1, :t2])
Z = zero(R)//1 # zero element of the fraction field of R
K, gs, D = TowerOfDifferentialFields([t1//x, (t2^2+1)*x*t1 + Z])
```

(Note: by adding `Z` to a polynomial we explicitely transform it to an element of the fraction field.)
