```
get_params(c::Chains; flatten=false)
```

Return all parameters packaged as a `NamedTuple`. Variables with a bracket in their name (as in "P[1]") will be grouped into the returned value as P.

Passing `flatten=true` will return a `NamedTuple` with keys ungrouped.

# Example

```jldoctest
julia> chn = Chains(1:5);

julia> x = get_params(chn);

julia> x.param_1
2-dimensional AxisArray{Int64,2,...} with axes:
    :iter, 1:1:5
    :chain, 1:1
And data, a 5×1 Matrix{Int64}:
 1
 2
 3
 4
 5
```
