```
randompreparations(n::Int, npreps::Int;
                   local_input_state = "Pauli")
```

量子回路に対して `npreps` 個のランダム入力状態を生成します。各 $n$-量子ビット入力状態は、以下のオプションに従って選択されます：

  * `local_input_states = "Pauli"`: $D=6^n$ パウリ固有状態
  * `local_input_states = "Tetra"`: $D=4^n$ 1量子ビット SIC-POVM

入力状態は、ユーザー定義のセットに設定することもでき、`local_input_states = ["A","B","C",...]` とし、単一量子ビット状態 $|A\rangle$, $|B\rangle$ が適切に定義されていると仮定します。
