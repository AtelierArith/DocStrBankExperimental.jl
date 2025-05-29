```
code_info(f::Function, tt::Type{T}; generated = true, debuginfo = :default) where T <: Tuple
code_info(f::Function, t::Type...; generated = true, debuginfo = :default)
```

Return lowered code for function `f` with tuple type `tt`. Equivalent to `InteractiveUtils.@code_lowered` – but a function call and requires a tuple type `tt` as input.
