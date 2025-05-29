```
print_tree(tree; kw...)
print_tree(io::IO, tree; kw...)
print_tree(f::Function, io::IO, tree; kw...)
print_tree(f::Function, g::Function, io::IO, tree; kw...)
```

Print a text representation of `tree` to the given `io` object.

# Arguments

  * `f::Function` - custom implementation of [`printnode`](@ref) to use. Should have the signature `f(io::IO, node; kw...)`.
  * `g::Function` -  custom implementation of [`print_child_key`](@ref) to use. Should have the

signature `g(io::IO, key;)`.

  * `io::IO` - IO stream to write to.
  * `tree` - tree to print.
  * `maxdepth::Integer = 5` - truncate printing of subtrees at this depth.
  * `indicate_truncation::Bool = true` - print a vertical ellipsis character beneath truncated nodes.
  * `charset::TreeCharSet` - [`TreeCharSet`](@ref) to use to print branches.
  * `printkeys::Union{Bool, Nothing}` - Whether to print keys of child nodes (using `pairs(children(node))`). A value of `nothing` uses [`printkeys_default`](@ref) do decide the behavior on a node-by-node basis.
  * `printnode_kw = (;)` - keyword arguments to forward to `f`.

# Examples

```julia
julia> tree = [1:3, "foo", [[[4, 5], 6, 7], 8]];

julia> print_tree(tree)
Vector{Any}
├─ UnitRange{Int64}
│  ├─ 1
│  ├─ 2
│  └─ 3
├─ "foo"
└─ Vector{Any}
   ├─ Vector{Any}
   │  ├─ Vector{Int64}
   │  │  ├─ 4
   │  │  └─ 5
   │  ├─ 6
   │  └─ 7
   └─ 8

julia> print_tree(tree, maxdepth=2)
Vector{Any}
├─ UnitRange{Int64}
│  ├─ 1
│  ├─ 2
│  └─ 3
├─ "foo"
└─ Vector{Any}
   ├─ Vector{Any}
   │  ⋮
   │
   └─ 8

julia> print_tree(tree, charset=AbstractTrees.ASCII_CHARSET)
Vector{Any}
+-- UnitRange{Int64}
|   +-- 1
|   +-- 2
|   \-- 3
+-- "foo"
\-- Vector{Any}
    +-- Vector{Any}
    |   +-- Vector{Int64}
    |   |   +-- 4
    |   |   \-- 5
    |   +-- 6
    |   \-- 7
    \-- 8
```
