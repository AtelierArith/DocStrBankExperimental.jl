```Julia
hubble(U::UnitSystem) = time(U,Hubble)
```

ハッブル宇宙膨張周波数パラメータ。

```Julia
julia> hubble(Metric)
2.1927112672380577e-18

julia> hubble(Hubble)
1

julia> hubble(Cosmological)
3.4872349617265916

julia> 𝟏/hubble(Metric)/year(Metric)
1.445155515342579e10
```
