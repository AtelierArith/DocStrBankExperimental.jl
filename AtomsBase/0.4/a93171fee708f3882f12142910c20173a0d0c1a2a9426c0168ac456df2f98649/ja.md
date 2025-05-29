```
atomic_number(sys::AbstractSystem, i)
atomic_number(species)
```

システム `sys` の原子番号のベクトル、または特定の `species` / `sys` の `i` 番目の種の原子番号。

[`atomic_number`](@ref) は `species` のタイプを特定することを意味することを意図しており（例えば、原子の場合は元素）、[`atomic_symbol`](@ref) はよりユニークな識別子を返すことがあります。例えば、重水素原子の場合、これは `:D` であるかもしれませんが、`atomic_number` はまだ `1` です。
