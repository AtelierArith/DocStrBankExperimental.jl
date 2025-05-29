```
gettreelength(n[, m])
```

Compute the length of the binary/quad tree `BitVector`.

# Arguments

  * `n::T where T<:Integer`: Array size at 1st dimension/Signal length for 1D-signals.
  * `m::T where T<:Integer`: Array size at 2nd dimension.

# Returns

  * `::T`: Length of binary/quad tree.

# Examples

```repl
using WaveletsExt

Utils.gettreelength(8)          # 7
Utils.gettreelength(8,8)        # 21
```
