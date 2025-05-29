```
dropout(x::Union{PyObject, Real, Array{<:Real}}, 
rate::Union{Real, PyObject}, training::Union{PyObject,Bool} = true; kwargs...)
```

`x`のエントリを`rate`の割合でランダムにドロップします。
