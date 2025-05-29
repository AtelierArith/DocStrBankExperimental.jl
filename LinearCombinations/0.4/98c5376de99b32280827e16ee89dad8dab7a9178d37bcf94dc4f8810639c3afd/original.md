```
regroup(a, b) -> Regroup
```

Return a `Regroup` object that can be used to rearrange the components of tensors and possibly other structures.

The actual rearrangement is specified by the two parameters `a` and `b`. Both are expression trees consisting of nested tuples of integers. These trees encode the structure of nested tensors, and the integers specify a mapping from the components of the nested source tensor to the nested target tensor. The labels for `a` and `b` can in fact be of any `isbits` type instead of `Int`, but they must be the same for `a` and `b`.

The return value `rg = regroup(a, b)` is a callable object. An argument `t` for `rg` must be a nested tensor of the same shape as the `a` tree, and the return value is a `Tensor` of the same shape as `b`. The components of the nested tensor `t` are permuted according to the labels.

If the components of `t` have non-zero degrees, then `rg(t)` additionally has a sign according to the usual sign rule: whenever two ojects `x` and `y` are swapped, then this incurs the sign `(-1)^(deg(x)*(deg(y)))`.

Moreover, `rg` is linear and can be called with linear combinations of tensors.

Note that for each `Regroup` element `rg`, Julia generates separate, efficient code for computing `rg(t)`.

See also [`swap`](@ref), [`regroup_inv`](@ref), [`Regroup`](@ref), [`LinearCombinations.DefaultCoefftype`](@ref).

# Examples

# Example without degrees

```jldoctest regroup
julia> rg = regroup(:( (1, (2, 3), 4) ), :( ((3, 1), (4, 2)) ))
Regroup{(1, (2, 3), 4),((3, 1), (4, 2))}

julia> t = Tensor("x", Tensor("y", "z"), "w")
"x"⊗("y"⊗"z")⊗"w"

julia> rg(t)
Linear1{Tensor{Tuple{Tensor{Tuple{String, String}}, Tensor{Tuple{String, String}}}}, Int64} with 1 term:
("z"⊗"x")⊗("w"⊗"y")
```

# Example with degrees

For simplicity, we define the degree of a `String` to be its length.

```jldoctest regroup
julia> LinearCombinations.deg(x::String) = length(x)

julia> rg(t)   # same rg and t as before
Linear1{Tensor{Tuple{Tensor{Tuple{String, String}}, Tensor{Tuple{String, String}}}}, Int64} with 1 term:
-("z"⊗"x")⊗("w"⊗"y")
```
