```
TopoChain(topo::FuncTopo, layers...)
```

Flux.Chainと似ていますが、呼び出される関数の順序/構造を定義するためにFuncTopoを使用する点が追加されています。

# 例

```jldoctest
julia> topo = @functopo x:x => a:x => b:(a, b) => c => o

julia> model = TopoChain(topo,
                Dense(32, 64),
                Dense(32, 64),
                (x, y) -> x .* y, 
                Dropout(0.1))

TopoChain(Dense(32, 64), Dense(32, 64), #5, Dropout(0.1)) は以下の関数合成を表します: 
function(x)
    a = Dense(32, 64)(x)
    b = Dense(32, 64)(x)
    c = #5(a, b)
    o = Dropout(0.1)(c)
    o
end
```
