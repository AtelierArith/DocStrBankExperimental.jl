```
RecombinedBSplineBasis{k, T}
```

Functional basis defined from the recombination of a [`BSplineBasis`](@ref) in order to satisfy certain homogeneous boundary conditions (BCs).

# Extended help

The basis recombination technique is a common way of applying BCs in Galerkin methods. It is described for instance in Boyd 2000 (ch. 6), in the context of a Chebyshev basis. In this approach, the original basis, $\{b_i(x), 1 ≤ i ≤ N\}$, is "recombined" into a new basis, $\{ϕ_j(x), 1 ≤ j ≤ M\}$, so that each basis function $ϕ_j$ individually satisfies the chosen BCs.

The length $M$ of the recombined basis is always smaller than the length $N$ of the original basis. The difference, $δ = N - M$, is equal to the number of boundary conditions. In the simplest (and most common) case, a single BC is applied on each boundary, leading to $δ = 2$. More generally, as described further below, it is possible to simultaneously impose different BCs, which further decreases the number of degrees of freedom (increasing $δ$).

Thanks to the local support of B-splines, basis recombination involves only a little portion of the original B-spline basis. For instance, since there is only one B-spline that is non-zero at each boundary, removing that function from the basis is enough to apply homogeneous Dirichlet BCs. Imposing BCs for derivatives is slightly more complex, but still possible.

Note that, when combining basis recombination with [collocation methods](@ref collocation-api), there must be **no** collocation points at the boundaries, or the resulting collocation matrices may not be invertible.

## Order of the boundary condition

In this section, we consider the simplest case where a single homogeneous boundary condition, $\mathrm{d}^n u / \mathrm{d}x^n = 0$, is to be satisfied by the basis.

The recombined basis requires the specification of a `Derivative` object determining the order of the homogeneous BCs to be applied at the two boundaries. Linear combinations of `Derivative`s are also supported. The order of the B-spline needs to be $k ≥ n + 1$, since a B-spline of order $k$ is a $C^{k - 1}$-continuous function (except on the knots where it is $C^{k - 1 - p}$, with $p$ the knot multiplicity).

Some usual choices are:

  * `Derivative(0)` sets homogeneous [Dirichlet BCs](https://en.wikipedia.org/wiki/Dirichlet_boundary_condition) ($u = 0$ at the boundaries) by removing the first and last B-splines, i.e. $ϕ_1 = b_2$;
  * `Derivative(1)` sets homogeneous [Neumann BCs](https://en.wikipedia.org/wiki/Neumann_boundary_condition) ($u' = 0$ at the boundaries) by adding the two first (and two last) B-splines, i.e. $ϕ_1 = b_1 + b_2$.
  * more generally, `α Derivative(0) + β Derivative(1)` sets homogeneous [Robin BCs](https://en.wikipedia.org/wiki/Robin_boundary_condition) by defining $ϕ_1$ as a linear combination of $b_1$ and $b_2$. Here it's important to note that `Derivative(1)` denotes the [normal derivative](https://en.wikipedia.org/wiki/Directional_derivative#Normal_derivative) at the boundary, $\frac{∂u}{∂n}$, which is equal to $-\frac{∂u}{∂x}$ on the left boundary.

Higher order BCs are also possible. For instance, `Derivative(2)` recombines the first three B-splines into two basis functions that satisfy $ϕ_1'' = ϕ_2'' = 0$ at the left boundary, while ensuring that lower and higher-order derivatives keep degrees of freedom at the boundary. Note that simply adding the first three B-splines, as in $ϕ_1 = b_1 + b_2 + b_3$, makes the first derivative vanish as well as the second one, which is unwanted.

For `Derivative(2)`, the chosen solution is to set $ϕ_i = α_i b_i + β_i b_{i + 1}$ for $i ∈ \{1, 2\}$. The $α_i$ and $β_i$ coefficients are chosen such that $ϕ_i'' = 0$ at the boundary. Moreover, they satisfy the (somewhat arbitrary) constraint $α_i + β_i = 2$ for each $i$, for consistency with the Neumann case described above. This generalises to higher order BCs. Note that, since each boundary function $ϕ_i$ is defined from only two neighbouring B-splines, its local support stays minimal, hence preserving the small bandwidth of the resulting matrices.

Finally, note that in the current implementation, it is not possible to impose different boundary conditions on both boundaries.

## Multiple boundary conditions

As an option, the recombined basis may simultaneously satisfy homogeneous BCs of different orders. In this case, a tuple of `Derivative`s must be passed.

For more details on the supported combinations of BCs, see the different `RecombinedBSplineBasis` constructors documented further below.

---

```
RecombinedBSplineBasis(B::BSplineBasis, op::AbstractDifferentialOp)
RecombinedBSplineBasis(B::BSplineBasis, op_left, op_right)
```

Construct `RecombinedBSplineBasis` from B-spline basis `B`, satisfying homogeneous boundary conditions (BCs) associated to the given differential operator.

The second case allows setting different BCs on each boundary.

For instance, `op = Derivative(0)` and `op = Derivative(1)` correspond to homogeneous Dirichlet and Neumann BCs, respectively.

Linear combinations of differential operators are also supported. For instance, `op = Derivative(0) + λ Derivative(1)` corresponds to homogeneous Robin BCs.

Higher-order derivatives are also allowed, being only limited by the order of the B-spline basis.

## Examples

```jldoctest RecombinedBSplineBasis
julia> B = BSplineBasis(BSplineOrder(4), -1:0.2:1)
13-element BSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]

julia> R_neumann = RecombinedBSplineBasis(B, Derivative(1))
11-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{1},)
 BCs right: (D{1},)

julia> R_robin = RecombinedBSplineBasis(B, Derivative(0) + 3Derivative(1))
11-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{0} + 3 * D{1},)
 BCs right: (D{0} + 3 * D{1},)
```

---

```
RecombinedBSplineBasis(B::BSplineBasis, ops)
RecombinedBSplineBasis(B::BSplineBasis, ops_left, ops_right)
```

Construct `RecombinedBSplineBasis` simultaneously satisfying homogeneous BCs associated to multiple differential operators.

Currently, the following cases are supported:

1. all derivatives up to order `m`:

    ```
     ops = (Derivative(0), ..., Derivative(m))
    ```

    This boundary condition is obtained by removing the first `m + 1` B-splines from the original basis.

    For instance, if `(Derivative(0), Derivative(1))` is passed, then the basis simultaneously satisfies homogeneous Dirichlet and Neumann BCs at the two boundaries. The resulting basis is $ϕ_1 = b_3, ϕ_2 = b_4, …, ϕ_{N - 4} = b_{N - 2}$.
2. an extension of the above, with an additional differential operator of order `n` at the end:

    ```
     ops = (Derivative(0), ..., Derivative(m), D(n))
    ```

    The operator `D(n)` may be a `Derivative`, or a linear combination of derivatives. The only restriction is that its maximum degree must satisfy `n ≥ m + 1`.

    One example is the combination of homogeneous Dirichlet BCs, $u = 0$ on the boundaries, with Robin BCs for the derivative, $u' + λ u'' = 0$, which corresponds to `ops = (Derivative(0), Derivative(1) + λ Derivative(2))`.
3. generalised natural boundary conditions:

    ```
     ops = Natural()
    ```

    This is equivalent to `ops = (Derivative(2), Derivative(3), ..., Derivative(k ÷ 2))` where `k` is the spline order (which must be even). See [`Natural`](@ref) for details.
4. "free" boundary conditions can simply be obtained by passing an empty tuple or `nothing`:

    ```
     ops = ()
     ops = nothing
    ```

    This means that no recombination will be performed. Therefore, if applied at the two boundaries, the resulting basis will be identical to the original basis, which is not very useful. In practice it can make sense to apply this on one of the boundaries, complemented by an actual boundary condition on the other end.

In the first two cases, the degrees of the differential operators must be in increasing order. For instance, `ops = (Derivative(1), Derivative(0))` fails with an error.

## Examples

```jldoctest RecombinedBSplineBasis
julia> ops = (Derivative(0), Derivative(1));


julia> R1 = RecombinedBSplineBasis(B, ops)
9-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{0}, D{1})
 BCs right: (D{0}, D{1})

julia> ops = (Derivative(0), Derivative(1) - 4Derivative(2));


julia> R2 = RecombinedBSplineBasis(B, ops)
9-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{0}, D{1} + -4 * D{2})
 BCs right: (D{0}, D{1} + -4 * D{2})

julia> R3 = RecombinedBSplineBasis(B, Natural())
11-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{2},)
 BCs right: (D{2},)
```
