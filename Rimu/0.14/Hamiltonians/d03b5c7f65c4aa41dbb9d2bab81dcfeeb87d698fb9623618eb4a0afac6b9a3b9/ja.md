```
Momentum(component=0; fold=true) <: AbstractHamiltonian
```

運動量演算子 $P̂$。

component 引数は、考慮されるアドレスのどの成分が対象となるかを制御します。値が 0 の場合、すべての成分の寄与が合計されます。`fold` が true の場合、運動量はブリルアンゾーンに折りたたまれます。

```jldoctest
julia> address = BoseFS((1, 0, 2, 1, 2, 1, 1, 3))
BoseFS{11,8}(1, 0, 2, 1, 2, 1, 1, 3)

julia> v = DVec(address => 10);

julia> rayleigh_quotient(Momentum(), DVec(address => 1))
-2.0

julia> rayleigh_quotient(Momentum(fold=false), DVec(address => 1))
14.0
```
