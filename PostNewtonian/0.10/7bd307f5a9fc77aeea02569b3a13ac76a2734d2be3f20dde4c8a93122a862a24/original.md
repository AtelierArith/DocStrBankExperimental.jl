```
PNExpansionParameter(pnsystem)
```

Create a [`PNTerm`](@ref) object representing the post-Newtonian expansion parameter $c$. This can be used to automatically create more complicated `PNTerm`s, which combine to form a [`PNExpansion`](@ref).  This is a simple but effective way to write PN formulas while automatically tracking the PN order of each term.
