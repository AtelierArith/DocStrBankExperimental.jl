```
convertUnit(val, codata; unitIn="Hartree", unitOut="xHz")
```

μHz,⋯ EHz, Hartree, Rydberg, J eV, cm-1, m-1, K, mK μK の単位変換

デフォルト入力: Hartree

デフォルト出力: xHz ∈ {μHz, mHz, Hz, kHz, MHz, GHz, THz, PHz, EHz}

#### 例:

```
julia> codata = castCodata(2018);
julia> convertUnit(1, codata; unitIn="Hz", unitOut="J")
Value(6.62607015e-34, "J")

julia> convertUnit(1, codata; unitIn="Hartree", unitOut="Hz")
Value(6.579683920501762e15, "Hz")

julia> f = convertUnit(1, codata) # デフォルト入力 (Hartree) と出力 (xHz);
julia> strf = strValue(f)
"6.57968 PHz"
```
