```
Base.sum(x::Convex.AbstractExpr; dims = :)
```

Sum `x`, optionally along a dimension `dims`.

## Examples

Sum all elements in an expression:

```jldoctest; filter=r"id: [0-9]+…[0-9]+"
julia> x = Variable(2, 2);

julia> atom = sum(x)
sum (affine; real)
└─ 2×2 real variable (id: 263…449)

julia> size(atom)
(1, 1)
```

Sum along the first dimension, creating a row vector:

```jldoctest; filter=r"id: [0-9]+…[0-9]+"
julia> x = Variable(2, 2);

julia> atom = sum(x; dims = 1)
* (affine; real)
├─ [1.0 1.0]
└─ 2×2 real variable (id: 143…826)

julia> size(atom)
(1, 2)
```

Sum along the second dimension, creating a columnn vector:

```jldoctest; filter=r"id: [0-9]+…[0-9]+"
julia> atom = sum(x; dims = 2)
* (affine; real)
├─ 2×2 real variable (id: 143…826)
└─ [1.0; 1.0;;]

julia> size(atom)
(2, 1)
```
