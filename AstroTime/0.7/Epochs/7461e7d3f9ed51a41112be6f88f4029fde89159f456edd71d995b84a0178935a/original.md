```
-(a::Epoch, b::Epoch)
```

Return the duration between epoch `a` and epoch `b`.

### Examples

```jldoctest; setup = :(using AstroTime)
julia> TAIEpoch(2018, 2, 6, 20, 45, 20.0) - TAIEpoch(2018, 2, 6, 20, 45, 0.0)
20.0 seconds
```
