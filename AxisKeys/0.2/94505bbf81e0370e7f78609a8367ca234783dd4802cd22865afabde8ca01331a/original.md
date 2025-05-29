```
wrapdims(A::NamedArray)
wrapdims(A::AxisArray)
```

Converts the wrapper from packages NamedArrays.jl or AxisArrays.jl. (Really it just guesses based on field names, since these packages are not loaded.)

# Examples

```
julia> using FreqTables, AxisKeys

julia> xs = vcat(repeat([1,2,3],4), [2,2,2,3]);

julia> ys = repeat('a':'d', 4);

julia> freqtable(xs, ys)
3×4 Named Matrix{Int64}
Dim1 ╲ Dim2 │ 'a'  'b'  'c'  'd'
────────────┼───────────────────
1           │   1    1    1    1
2           │   2    2    2    1
3           │   1    1    1    2

julia> wrapdims(ans)
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Dim1 ∈ 3-element Vector{Int64}
→   Dim2 ∈ 4-element Vector{Char}
And data, 3×4 Matrix{Int64}:
      ('a')  ('b')  ('c')  ('d')
 (1)   1      1      1      1
 (2)   2      2      2      1
 (3)   1      1      1      2
```
