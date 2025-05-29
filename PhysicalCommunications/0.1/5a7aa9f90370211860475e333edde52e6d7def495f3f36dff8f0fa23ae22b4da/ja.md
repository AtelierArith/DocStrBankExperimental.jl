```
sequence(t::SequenceGenerator; seed::Integer=11, len::Int=-1, output::DataType=Int)
```

長さ `len` のビット列を定義するイテラブルオブジェクトを作成します。

入力:

  * t: ビット列を生成するために使用されるアルゴリズムのタイプを定義するインスタンス。
  * seed: 列を構築するために使用されるレジスタの初期値。
  * len: 列のビット数。
  * output: 列の要素に使用されるデータ型（典型的な値は `Int` または `Bool`）。

初期レジスタ値 `11` でシードされた最大長LFSRアルゴリズムを使用して構築されたPRBS-`31` パターンの最初の `1000` ビットを返す例:

```
pattern = collect(sequence(MaxLFSR(31), seed=11, len=1000, output=Bool)).
```
