```julia
isBandGapped(H::Hamiltonian ; tol::Float64 = 1e-3) --> BitMatrix
```

行列の行と列に対応するバンドがギャップがある場合（許容値より大きい）には`true`としてマークされたブール値の行列を返し、それ以外の場合は`false`を返します。
