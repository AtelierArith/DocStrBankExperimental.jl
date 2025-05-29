```
uint_map(x, order::Ordering)::Unsigned
```

`x`を符号なし整数にマップし、ソート順を維持します。

このマップは[`uint_unmap`](@ref)で逆にできる必要があるため、`isless(order, a, b)`は`a, b <: typeof(x)`に対して線形順序でなければなりません。`isless(order, a, b) === (uint_map(a, order) < uint_map(b, order))`および`x === uint_unmap(typeof(x), uint_map(x, order), order)`を満たします。

関連情報: [`UIntMappable`](@ref) [`uint_unmap`](@ref)
