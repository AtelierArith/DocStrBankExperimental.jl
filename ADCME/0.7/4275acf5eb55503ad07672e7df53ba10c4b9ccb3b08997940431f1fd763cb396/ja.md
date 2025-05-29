```
adjoint(o::PyObject; kwargs...)
```

`o`の共役随伴を返します。`o`の次元が2より大きい場合、最後の2つの次元のみが置換されます。すなわち、`permutedims(o, [1,2,...,n,n-1])`です。
