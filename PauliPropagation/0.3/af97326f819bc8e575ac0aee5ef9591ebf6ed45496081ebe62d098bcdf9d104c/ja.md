```
PauliRotation(symbols::Vector{Symbol}, qinds::Vector{Int})
PauliRotation(symbol::Symbol, qinds::Int)
```

パラメータ化されたパウリ回転で、パウリ文字列 `symbols` が量子ビット `qinds` に作用します。例えば、PauliRotation(:X, 2) または PauliRotation([:X, :Y], [1, 2]) のようになります。
