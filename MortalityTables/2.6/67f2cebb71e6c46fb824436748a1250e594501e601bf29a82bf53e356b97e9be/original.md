```
omega(x)
ω(x)
```

Returns the last index of the given vector. For mortality vectors this means the last attained age for which a rate is defined.

Note that `omega` can vary depending on the issue age for a select table, and that a select `omega` may differ from the table's ultimate `omega`.

ω is aliased to omega, but un-exported. To use, do `using MortalityTables: ω` when importing or call `MortalityTables.ω()`

# Examples

```julia-repl
julia> qs = UltimateMortality([0.1,0.3,0.6,1]);
julia> omega(qs)
3

julia> qs = UltimateMortality([0.1,0.3,0.6,1],start_age=10);
julia> omega(qs)
13

```
