```
allcombinations(DataFrame, pairs::Pair...)
allcombinations(DataFrame; kwargs...)
```

Create a `DataFrame` from all combinations of values in passed arguments. The first passed values vary fastest.

Arguments associating a column name with values to expand can be specified either as `Pair`s passed as positional arguments, or as keyword arguments. Column names must be `Symbol`s or strings and must be unique.

Column value can be a vector which is consumed as is or an object of any other type (except `AbstractArray`). In the latter case the passed value is treated as having length one for expansion. As a particular rule values stored in a `Ref` or a `0`-dimensional `AbstractArray` are unwrapped and treated as having length one.

See also: [`crossjoin`](@ref) can be used to get the cartesian product of rows from passed data frames.

# Examples

```jldoctest
julia> allcombinations(DataFrame, a=1:2, b='a':'c')
6×2 DataFrame
 Row │ a      b
     │ Int64  Char
─────┼─────────────
   1 │     1  a
   2 │     2  a
   3 │     1  b
   4 │     2  b
   5 │     1  c
   6 │     2  c

julia> allcombinations(DataFrame, "a" => 1:2, "b" => 'a':'c', "c" => "const")
6×3 DataFrame
 Row │ a      b     c
     │ Int64  Char  String
─────┼─────────────────────
   1 │     1  a     const
   2 │     2  a     const
   3 │     1  b     const
   4 │     2  b     const
   5 │     1  c     const
   6 │     2  c     const
```
