```
CartesianGrids.Nodes
```

`CartesianGrids.Nodes` は、デュアルセルまたはプライマリセルの中心にあるスカラー値データのラッパーです。`CartesianGrids.Nodes` 型は、他の配列と同様にインデックスを使用してアクセスでき、`size`、`similar`、`zero` 関数の使用を可能にします。

# コンストラクタ

  * `CartesianGrids.Nodes(C,dims)` は、次元 `dims`（タプル）上のグリッドで、タイプ `C`（`C` は `Dual` または `Primal` のいずれか）におけるセルにゼロのフィールドを作成します。`dims` は、`C` が `Primal` であっても、グリッド上のデュアルセルの数を表すことに注意してください。
  * `CartesianGrids.Nodes(C,w)` は、同じ構築を行いますが、グリッドのサイズを決定するために `GridData` 型の既存のフィールドデータ `w` を使用します。
  * `dtype=` キーワードを追加することで、フィールドデータのデータ型を変更できます。デフォルトは `Float64` ですが、例えば `ComplexF64` に変更することができます。
