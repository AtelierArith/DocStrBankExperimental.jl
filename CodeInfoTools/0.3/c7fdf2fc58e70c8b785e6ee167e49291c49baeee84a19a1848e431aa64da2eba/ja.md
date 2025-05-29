```
code_info(f::Function, tt::Type{T}; generated = true, debuginfo = :default) where T <: Tuple
code_info(f::Function, t::Type...; generated = true, debuginfo = :default)
```

関数 `f` のタプル型 `tt` に対する低下したコードを返します。`InteractiveUtils.@code_lowered` と同等ですが、関数呼び出しであり、入力としてタプル型 `tt` を必要とします。
