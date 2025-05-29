```
Gas(name, short_name; γ, M) -> Gas
```

新しいGasをインスタンス化し、名前、短縮名、断熱指数、およびモル質量を提供します。その他のガス特性、ガス定数、定圧/定積の比熱、および原子/分子の質量（kg単位）が計算されます。

```jldoctest;setup = :(using HallThruster: Gas)
julia> Gas("Xenon", "Xe", γ = 5/3, M = 83.798)
Xenon
```
