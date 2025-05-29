```
Barycentric(node, value, weight, wf=value .* weight; stats=missing)
```

Construct a `Barycentric` rational function.

# Arguments

  * `node::Vector`: interpolation nodes
  * `value::Vector`: values at the interpolation nodes
  * `weight::Vector`: barycentric weights

# Keywords

  * `wf::Vector = value .* weight`: weights times values

# Returns

  * `::Barycentric`: a barycentric rational interpolating function

# Examples

```jldoctest
julia> r = Barycentric([1, 2, 3], [1, 2, 3], [1/2, -1, 1/2])
Barycentric function with 3 nodes and values:
    1.0=>1.0,  2.0=>2.0,  3.0=>3.0

julia> r(1.5)
1.5
```
