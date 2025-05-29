```julia
DiagonalizeHamiltonian!(H::LatticeHamiltonian)
```

`H`に格納されたハミルトニアンを対角化し、固有値と固有ベクトルをそれぞれ`H.bands`と`H.states`に格納します。また、バンド幅も計算します。
