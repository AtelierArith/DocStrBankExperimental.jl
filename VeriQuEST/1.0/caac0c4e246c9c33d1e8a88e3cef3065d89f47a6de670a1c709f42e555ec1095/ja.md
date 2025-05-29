```
get_updated_ϕ!(RountType, QubitType, QubitIOType, client_meta_graph, qubit)
```

指定された量子ビットのϕ値を`client_meta_graph`内で`update_ϕ!`関数を使用して更新し、その後更新されたϕ値を取得します。

# 引数

  * `RountType`: 計算ラウンドのタイプ。
  * `QubitType`: 計算量子ビットのタイプ。
  * `QubitIOType`: 入力量子ビットのタイプ。
  * `client_meta_graph`: 更新されるグラフ。
  * `qubit`: ϕ値を更新し取得するためのグラフ内の量子ビット。

# 戻り値

  * 指定された量子ビットの更新されたϕ値。

# 例

```julia
updated_ϕ = get_updated_ϕ!(ComputationRound, ComputationQubit, NoInputQubits, client_meta_graph, qubit) # グラフ内の指定された量子ビットのϕ値を更新し、それを取得します
```
