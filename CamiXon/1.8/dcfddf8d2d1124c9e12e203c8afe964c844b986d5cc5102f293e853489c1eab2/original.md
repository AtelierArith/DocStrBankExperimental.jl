```
convertUnit(val, codata; unitIn="Hartree", unitOut="xHz")
```

Unit conversion between μHz,⋯ EHz, Hartree, Rydberg, J eV, cm-1, m-1, K, mK μK

default input: Hartree

default output: xHz ∈ {μHz, mHz, Hz, kHz, MHz, GHz, THz, PHz, EHz}

#### Example:

```
julia> codata = castCodata(2018);
julia> convertUnit(1, codata; unitIn="Hz", unitOut="J")
Value(6.62607015e-34, "J")

julia> convertUnit(1, codata; unitIn="Hartree", unitOut="Hz")
Value(6.579683920501762e15, "Hz")

julia> f = convertUnit(1, codata) # default input (Hartree) and output (xHz);
julia> strf = strValue(f)
"6.57968 PHz"
```
