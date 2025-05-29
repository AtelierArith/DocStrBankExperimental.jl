```
values_as(varinfo[, Type])
```

Return the values/realizations in `varinfo` as `Type`, if implemented.

If no `Type` is provided, return values as stored in `varinfo`.

# Examples

`SimpleVarInfo` with `NamedTuple`:

```jldoctest
julia> data = (x = 1.0, m = [2.0]);

julia> values_as(SimpleVarInfo(data))
(x = 1.0, m = [2.0])

julia> values_as(SimpleVarInfo(data), NamedTuple)
(x = 1.0, m = [2.0])

julia> values_as(SimpleVarInfo(data), OrderedDict)
OrderedDict{VarName{sym, typeof(identity)} where sym, Any} with 2 entries:
  x => 1.0
  m => [2.0]

julia> values_as(SimpleVarInfo(data), Vector)
2-element Vector{Float64}:
 1.0
 2.0
```

`SimpleVarInfo` with `OrderedDict`:

```jldoctest
julia> data = OrderedDict{Any,Any}(@varname(x) => 1.0, @varname(m) => [2.0]);

julia> values_as(SimpleVarInfo(data))
OrderedDict{Any, Any} with 2 entries:
  x => 1.0
  m => [2.0]

julia> values_as(SimpleVarInfo(data), NamedTuple)
(x = 1.0, m = [2.0])

julia> values_as(SimpleVarInfo(data), OrderedDict)
OrderedDict{Any, Any} with 2 entries:
  x => 1.0
  m => [2.0]

julia> values_as(SimpleVarInfo(data), Vector)
2-element Vector{Float64}:
 1.0
 2.0
```

`VarInfo` with `NamedTuple` of `Metadata`:

```jldoctest
julia> # Just use an example model to construct the `VarInfo` because we're lazy.
       vi = DynamicPPL.typed_varinfo(DynamicPPL.TestUtils.demo_assume_dot_observe());

julia> vi[@varname(s)] = 1.0; vi[@varname(m)] = 2.0;

julia> # For the sake of brevity, let's just check the type.
       md = values_as(vi); md.s isa Union{DynamicPPL.Metadata, DynamicPPL.VarNamedVector}
true

julia> values_as(vi, NamedTuple)
(s = 1.0, m = 2.0)

julia> values_as(vi, OrderedDict)
OrderedDict{VarName{sym, typeof(identity)} where sym, Float64} with 2 entries:
  s => 1.0
  m => 2.0

julia> values_as(vi, Vector)
2-element Vector{Float64}:
 1.0
 2.0
```

`VarInfo` with `Metadata`:

```jldoctest
julia> # Just use an example model to construct the `VarInfo` because we're lazy.
       vi = DynamicPPL.untyped_varinfo(DynamicPPL.TestUtils.demo_assume_dot_observe());

julia> vi[@varname(s)] = 1.0; vi[@varname(m)] = 2.0;

julia> # For the sake of brevity, let's just check the type.
       values_as(vi) isa Union{DynamicPPL.Metadata, Vector}
true

julia> values_as(vi, NamedTuple)
(s = 1.0, m = 2.0)

julia> values_as(vi, OrderedDict)
OrderedDict{VarName{sym, typeof(identity)} where sym, Float64} with 2 entries:
  s => 1.0
  m => 2.0

julia> values_as(vi, Vector)
2-element Vector{Real}:
 1.0
 2.0
```
