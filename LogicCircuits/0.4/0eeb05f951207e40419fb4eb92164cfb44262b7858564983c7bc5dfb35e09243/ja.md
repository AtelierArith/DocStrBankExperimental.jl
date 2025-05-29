```
foldup_aggregate(node::LogicCircuit, 
    f_con::Function, 
    f_lit::Function, 
    f_a::Function, 
    f_o::Function, 
    ::Type{T})::T where T
```

回路に対してボトムアップで関数を計算します。`f_con`は定数ゲートに対して呼び出され、`f_lit`はリテラルゲートに対して呼び出され、`f_a`は論理積に対して呼び出され、`f_o`は論理和に対して呼び出されます。型`T`の値は回路を上に渡され、子からの集約ベクトルで`f_a`と`f_o`に渡されます。
