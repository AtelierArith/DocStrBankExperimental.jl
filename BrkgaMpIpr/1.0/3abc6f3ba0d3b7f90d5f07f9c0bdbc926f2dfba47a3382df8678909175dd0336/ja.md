```
set_bias_custom_function!(brkga_data::BrkgaData, bias_function::Function)
```

新しいバイアス関数を設定して、交配中に染色体をランク付けするために使用します。**これは正の非増加関数でなければなりません**。Float64を返す必要があります。すなわち、`f(::Int64)::Float64` であり、`f(i) ≥ 0` かつ `f(i) ≥ f(i+1)` である必要があります（`i ∈ [1..total_parents]`）。例えば、以下は逆二次関数を設定します：

```julia
set_bias_custom_function!(brkga_data, x -> 1.0 / (x * x))
```

# 例外

  * `ArgumentError`: 関数が非増加の正の関数でない場合。
