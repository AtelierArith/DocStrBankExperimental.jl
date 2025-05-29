```
atomic_symbol(sys::AbstractSystem, i)
atomic_symbol(species)
```

システム `sys` の原子記号のベクトル、または特定の `species` / `sys` の `i` 番目の種の原子記号。

意図は、[`atomic_number`](@ref) が `species` のタイプを特定する意味を持つ（例えば、原子の場合の元素）一方で、[`atomic_symbol`](@ref) はよりユニークな識別子を返すことです。例えば、重水素原子の場合、これは `:D` である可能性がありますが、`atomic_number` はまだ `1` です。
