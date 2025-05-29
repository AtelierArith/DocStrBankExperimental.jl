```
groundstate(eig::HamiltonianEigensystem)
groundstate(ham::Hamiltonian)
```

ハミルトニアンの基底状態を見つけます。状態を返します。

## 例

```julia
eig = diagonalize(ham)
ψ = groundstate(eig)
```
