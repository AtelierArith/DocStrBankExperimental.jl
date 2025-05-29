```
num_indep_components(::Type{<:Number})
num_indep_components(a::Number)
```

`Number`の独立成分の数、すなわち`num_components`から対称性や制約によって他の成分から決定される成分の数を引いたものです。

例えば、`TensorValue{3,3}`は9つの独立成分を持ち、`SymTensorValue{3}`は6つ、`SymTracelessTensorValue{3}`は5つの独立成分を持っています。しかし、これらはすべて9つの（非独立）成分を持っています。
