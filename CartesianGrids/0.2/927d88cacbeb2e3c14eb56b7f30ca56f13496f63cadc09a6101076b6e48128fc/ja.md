```
NodePair
```

`NodePair` は、双対セルと原始セルのノードにあるベクトル値データのラッパーです。`NodePair` 型のデータには、ベクトル場の成分のためのフィールド `u` と `v` があります。これらは、原始セルの面の1つを中心とした仮想セルの面を形成するノード上のベクトル場の法線成分です。

# コンストラクタ

  * `NodePair(C,dims)` は、タイプ `C`（`C` は `Dual` または `Primal` のいずれか）で、次元 `dims` のグリッド上にゼロのベクトル場を作成します。`dims` はグリッド上の双対セルの数を表します。
  * `NodePair(C,w)` は同じ構築を行いますが、グリッドのサイズを決定するために `GridData` 型の既存のフィールドデータ `w` を使用します。
  * `dtype=` キーワードを追加することで、フィールドデータのデータ型を変更できます。デフォルトは `Float64` ですが、例えば `ComplexF64` に変更することもできます。
