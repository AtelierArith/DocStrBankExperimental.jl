```
PauliString(nqubits::Int, pauli::Symbol, qind::Integer, coeff=1.0)
PauliString(nqubits::Int, paulis::Vector{Symbol}, qinds::Vector{Integer}, coeff=1.0)
```

`nqubits`量子ビットの`Symbol`（:I, :X, :Y, :Z）または`Vector{Symbol}`からの`PauliString`のコンストラクタ。これらのシンボルのインデックスを`qind`または`qinds`として提供します。パウリ和におけるパウリ文字列の係数はデフォルトで1.0です。
