```
findgroundstate(eig::HamiltonianEigensystem)
findgroundstate(ham::Hamiltonian)
```

ハミルトニアンの基底状態を見つけます。エネルギーと状態を返します。

## 例

```julia
eig = diagonalize(ham)
E, ψ = findgroundstate(eig)
```
