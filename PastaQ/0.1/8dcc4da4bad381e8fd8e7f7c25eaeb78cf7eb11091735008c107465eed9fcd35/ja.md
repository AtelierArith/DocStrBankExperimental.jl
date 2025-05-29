```
fullpreparations(n::Int; local_input_states = "Pauli")
```

$$
M
$$

個の1量子ビット状態から構成された$D=M^n$状態の完全な$n$量子ビット入力状態のセットを生成します。定義済みのオプション：

  * `local_input_states = "Pauli"`: $D=6^n$ パウリ固有状態
  * `local_input_states = "Tetra"`: $D=4^n$ 1量子ビットSIC-POVM
