c = split_con(s::SeisCon, inds)

Creates a new SeisCon object `c` without copying by referencing `s.blocks[inds]`

`inds` can be an array of indicies, a range, or a scalar.

# Example

```julia-repl
julia> b = split_con(s, 1:10);
julia> c = split_con(b, [1; 7; 9]);
julia> d = split_con(c, 1);
```

And we can confirm that `d` and `s` reference the same place in memory.

```julia-repl
julia> s.blocks[1] === d.blocks[1]
true
```
