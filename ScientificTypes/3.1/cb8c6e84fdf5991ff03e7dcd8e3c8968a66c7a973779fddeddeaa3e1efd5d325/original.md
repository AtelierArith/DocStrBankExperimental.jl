```
coerce(A, S)
```

Return new version of the array `A` whose scientific element type is `S`.

```
julia> v = coerce([3, 7, 5], Continuous)
3-element Vector{Float64}:
 3.0
 7.0
 5.0

julia> scitype(v)
AbstractVector{Continuous}

```

```
coerce(X, specs...; tight=false, verbosity=1)
```

Given a table `X`, return a copy of `X`, ensuring that the element scitypes of the columns match the new specification, `specs`. There are three valid specifications:

(i) one or more `column_name=>Scitype` pairs:

```
coerce(X, col1=>Scitype1, col2=>Scitype2, ... ; verbosity=1)
```

(ii) one or more `OldScitype=>NewScitype` pairs (`OldScitype` covering both the `OldScitype` and `Union{Missing,OldScitype}` cases):

```
coerce(X, OldScitype1=>NewScitype1, OldScitype2=>NewScitype2, ... ; verbosity=1)
```

(iii) a dictionary of scientific types keyed on column names:

```
coerce(X, d::AbstractDict{<:ColKey, <:Type}; verbosity=1)
```

where `ColKey = Union{Symbol,AbstractString}`.

### Examples

Specifying  `column_name=>Scitype` pairs:

```
using CategoricalArrays, DataFrames, Tables
X = DataFrame(name=["Siri", "Robo", "Alexa", "Cortana"],
              height=[152, missing, 148, 163],
              rating=[1, 5, 2, 1])
Xc = coerce(X, :name=>Multiclass, :height=>Continuous, :rating=>OrderedFactor)
schema(Xc).scitypes # (Multiclass, Continuous, OrderedFactor)
```

Specifying `OldScitype=>NewScitype` pairs:

```
X  = (x = [1, 2, 3],
      y = rand(3),
      z = [10, 20, 30])
Xc = coerce(X, Count=>Continuous)
schema(Xfixed).scitypes # (Continuous, Continuous, Continuous)
```
