```
recode(a::AbstractArray[, default::Any], pairs::Pair...)
```

Return a copy of `a`, replacing elements matching a key of `pairs` with the corresponding value. The type of the array is chosen so that it can hold all recoded elements (but not necessarily original elements from `a`).

For each `Pair` in `pairs`, if the element is equal to (according to `isequal`) or `in` the key (first item of the pair), then the corresponding value (second item) is used. If the element matches no key and `default` is not provided or `nothing`, it is copied as-is; if `default` is specified, it is used in place of the original element. If an element matches more than one key, the first match is used.

```
recode(a::CategoricalArray[, default::Any], pairs::Pair...)
```

If `a` is a `CategoricalArray` then the ordering of resulting levels is determined by the order of passed `pairs` and `default` will be the last level if provided.

# Examples

```jldoctest
julia> using CategoricalArrays

julia> recode(1:10, 1=>100, 2:4=>0, [5; 9:10]=>-1)
10-element Vector{Int64}:
 100
   0
   0
   0
  -1
   6
   7
   8
  -1
  -1

```

```
 recode(a::AbstractArray{>:Missing}[, default::Any], pairs::Pair...)
```

If `a` contains missing values, they are never replaced with `default`: use `missing` in a pair to recode them. If that's not the case, the returned array will accept missing values.

# Examples

```jldoctest
julia> using CategoricalArrays

julia> recode(1:10, 1=>100, 2:4=>0, [5; 9:10]=>-1, 6=>missing)
10-element Vector{Union{Missing, Int64}}:
 100
   0
   0
   0
  -1
    missing
   7
   8
  -1
  -1    

```
