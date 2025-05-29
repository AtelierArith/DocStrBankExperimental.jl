```
@functopo structure
```

Create a `FuncTopo` to apply functions according to the given `structure`.

# Example

```jldoctest
julia> @functopo (x1, x2):(x1, x2) => a:x1 => b:(a, b) => c => o
FuncTopo{"(x1, x2):(x1, x2) => (a:x1 => (b:(a, b) => (c => o)))"}
function(model, x1, x2)
    a = model[1](x1, x2)
    b = model[2](x1)
    c = model[3](a, b)
    o = model[4](c)
    o
end
```
