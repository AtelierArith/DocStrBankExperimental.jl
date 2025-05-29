```
CellPotts(space, initialCellState, penalties)
```

細胞ポッツシミュレーションを実行するための情報を保持するデータコンテナです。

3つの入力が必要です：

  * `space` – セルが存在できる領域で、`CellSpace()`を使用して生成されます。
  * `state` – 行がセル、列がセルのプロパティであるテーブルで、`CellState()`を使用して生成されます。
  * `penalties` – モデルに追加するペナルティのベクトルです。
