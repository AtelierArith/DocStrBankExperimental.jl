```
foldup(node::LogicCircuit, 
    f_con::Function, 
    f_lit::Function, 
    f_a::Function, 
    f_o::Function)::T where {T}
```

回路上でボトムアップで関数を計算します。 `f_con` は定数ゲートで呼び出され、`f_lit` はリテラルゲートで呼び出され、`f_a` は論理積で呼び出され、`f_o` は論理和で呼び出されます。型 `T` の値は回路を上に渡され、子からのコールバックを通じて `f_a` と `f_o` に渡されます。
