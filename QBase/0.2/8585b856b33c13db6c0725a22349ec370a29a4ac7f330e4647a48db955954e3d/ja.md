```
mirror_symmetric_qubit_3povm( θ :: Real ) :: POVM{Float64}
```

三つのミラー対称量子ビット状態に整列した `POVM` を構築します。最初の測定は $|0\rangle$ 状態に整列しており、残りの二つは z 軸に対して対称です。

引数 `θ` が [π/4,π/2] に含まれない場合、`DomainError` がスローされます。
