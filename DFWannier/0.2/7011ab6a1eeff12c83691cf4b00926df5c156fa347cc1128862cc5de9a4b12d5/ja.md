```
read_hamiltonian(chk::NamedTuple, eigvals::Matrix)
```

`chk`のWannier90チェックポイント情報と[`read_eig`]で読み込んだDFT `eigenvals`を使用して、[`TBHamiltonian`](@ref TBOperator)を構築します。
