```
map(ex, args)
```

Return an instance of the map type corresponding to the given expression.

### Input

  * `ex`   – an expression defining the map, in the form of an anonymous function
  * `args` – additional optional arguments

### Output

A map that best matches the given expression.

### Examples

Let us first create a linear map using this macro:

```jldoctest
julia> @map x -> [1 0; 0 0]*x
LinearMap{Int64, Matrix{Int64}}([1 0; 0 0])
```

We can create an affine system as well:

```jldoctest
julia> @map x -> [1 0; 0 0]*x + [2, 0]
AffineMap{Int64, Matrix{Int64}, Vector{Int64}}([1 0; 0 0], [2, 0])
```

Additional arguments can be passed to `@map` using the function-call form, i.e. separating the arguments by commas, and using parentheses around the macro call. For example, an identity map of dimension 5 can be defined as:

```jldoctest
julia> @map(x -> x, dim=5)
IdentityMap(5)
```

A state constraint on such map can be specified passing the additional argument `x ∈ X`.

An identity map can alternatively be created by giving a the size of the identity matrix as `Id(n)`, for example:

```jldoctest
julia> @map x -> Id(5)*x
IdentityMap(5)
```
