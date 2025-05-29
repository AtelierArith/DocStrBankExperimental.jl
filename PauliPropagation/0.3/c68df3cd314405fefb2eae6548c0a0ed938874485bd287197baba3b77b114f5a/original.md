```
symboltoint(pstr::Union{Vector{Symbol}, Symbol})
```

Maps a symbol or a vector of symbols `pstr` to an integer Pauli string.

# Example

```
symboltoint([:X, :I])

# output

0x01
```
