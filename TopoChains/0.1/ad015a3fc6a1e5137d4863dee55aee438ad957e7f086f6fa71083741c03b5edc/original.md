```
TopoChain(topo::FuncTopo, layers...)
```

Similar to a Flux.Chain, with the addition of the use of an FuncTopo to define the order/structure of the functions called.

# Example

```jldoctest
julia> topo = @functopo x:x => a:x => b:(a, b) => c => o

julia> model = TopoChain(topo,
                Dense(32, 64),
                Dense(32, 64),
                (x, y) -> x .* y, 
                Dropout(0.1))

TopoChain(Dense(32, 64), Dense(32, 64), #5, Dropout(0.1)) representing the following function composition: 
function(x)
    a = Dense(32, 64)(x)
    b = Dense(32, 64)(x)
    c = #5(a, b)
    o = Dropout(0.1)(c)
    o
end
```
