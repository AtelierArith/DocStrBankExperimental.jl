```
CartesianGrids.YEdges
```

`CartesianGrids.YEdges` は、デュアルセルまたはプライマリセルの中心にあるスカラー値データのラッパーです。`CartesianGrids.YEdges` 型は、他の配列と同様にインデックスを使用してアクセスでき、`size`、`similar`、`zero` 関数の使用を可能にします。

# コンストラクタ

  * `CartesianGrids.YEdges(C,dims)` は、次元 `dims`（タプル）を持つグリッド上の `C` 型（`C` は `Dual` または `Primal` のいずれか）でゼロのフィールドを作成します。`dims` は、`C` が `Primal` であっても、グリッド上のデュアルセルの数を表すことに注意してください。
  * `CartesianGrids.YEdges(C,w)` は、同じ構築を行いますが、グリッドのサイズを決定するために `GridData` 型の既存のフィールドデータ `w` を使用します。
  * `dtype=` キーワードを追加することで、フィールドデータのデータ型を変更できます。デフォルトは `Float64` ですが、例えば `ComplexF64` に変更することができます。
