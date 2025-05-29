```
add!(psum::PauliSum, pauli::Symbol, qind::Integer, coeff=1.0)
add!(psum::PauliSum, paulis::Vector{Symbol}, qinds::Vector{Integer}, coeff=1.0)
```

`PauliSum` `psum` にパウリ文字列を追加します。`psum` はインプレースで変更されます。パウリ文字列を `Symbol` (:I, :X, :Y, :Z) または `Vector{Symbol}` として提供してください。それらのシンボルのインデックスまたはインデックスを `qind` または `qinds` として提供してください。パウリ和におけるパウリ文字列の係数はデフォルトで 1.0 です。
