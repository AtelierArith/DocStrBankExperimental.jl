```
function collective_coupling(op, num_qubit; sp = false, unit = :h)
```

各量子ビットに演算子 `op` を持つ `ConstantCouplings` オブジェクトを作成します。`op` はパウリ行列の1つの文字列表現です。`num_qubit` は量子ビットの総数です。`sp` はスパース行列を使用するかどうかを設定します。`unit` は単位を設定します – `:h` または `:ħ`。
