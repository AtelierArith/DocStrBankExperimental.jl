```
TorQuadModule
```

# Examples

```jldoctest
julia> A = matrix(ZZ, [[2,0,0,-1],[0,2,0,-1],[0,0,2,-1],[-1,-1,-1,2]]);

julia> L = integer_lattice(gram = A);

julia> T = Hecke.discriminant_group(L)
Finite quadratic module
  over integer ring
Abelian group: (Z/2)^2
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[   1   1//2]
[1//2      1]
```

We represent torsion quadratic modules as quotients of $\mathbb{Z}$-lattices by a full rank sublattice.

We store them as a $\mathbb{Z}$-lattice `M` together with a projection `p : M -> A` onto an abelian group `A`. The bilinear structure of `A` is induced via `p`, that is `<a, b> = <p^-1(a), p^-1(a)>` with values in $\mathbb{Q}/n\mathbb{Z}$, where $n$ is the modulus and depends on the kernel of `p`.

Elements of A are basically just elements of the underlying abelian group. To move between `M` and `A`, we use the `lift` function `lift : M -> A` and coercion `A(m)`.

# Examples

```jldoctest
julia> R = rescale(root_lattice(:D,4),2);

julia> D = discriminant_group(R);

julia> A = abelian_group(D)
(Z/2)^2 x (Z/4)^2

julia> d = D[1]
Element
  of finite quadratic module: (Z/2)^2 x (Z/4)^2 -> Q/2Z
with components [1 0 0 0]

julia> d == D(A(d))
true

julia> lift(d)
4-element Vector{QQFieldElem}:
 1
 1
 3//2
 1
```

N.B. Since there are no elements of $\mathbb{Z}$-lattices, we think of elements of `M` as elements of the ambient vector space. Thus if `v::Vector` is such an element then the coordinates with respec to the basis of `M` are given by `solve(basis_matrix(M), v; side = :left)`.
