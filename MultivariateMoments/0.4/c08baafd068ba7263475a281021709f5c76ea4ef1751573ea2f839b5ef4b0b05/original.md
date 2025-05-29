```
struct UserRank <: RankCheck
    pagesize::Int
end
```

The user chooses the rank given the singular values in a `REPL.TerminalMenus.RadioMenu` of page size `pagesize`.

## Example

```julia
julia> rank_from_singular_values([1, 1e-1, 5e-2, 1e-5, 5e-6], UserRank())
Choose the last significant singular value:
   1.0
   0.1
 > 0.05
   1.0e-5
   5.0e-6
3
```
