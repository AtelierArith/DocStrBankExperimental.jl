```
struct ArraySymbolic <: SymbolicTypeTrait end
```

型がシンボリック配列であることを示すトレイト。シンボリック配列に対して `collect` を呼び出すと、配列内の各要素に対して `ScalarSymbolic` 変数を含む `AbstractArray` が返される必要があり、表現される配列と同じ形状でなければなりません。例えば、`a` が 2x2 行列を表すシンボリック配列である場合、`collect(a)` はスカラーシンボリック変数の 2x2 配列を返さなければなりません。

参照: [`ScalarSymbolic`](@ref), [`NotSymbolic`](@ref), [`symbolic_type`](@ref)
