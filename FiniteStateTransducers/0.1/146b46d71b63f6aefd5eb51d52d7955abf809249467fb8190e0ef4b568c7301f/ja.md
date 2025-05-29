`add_arc!(fst, src, dest, ilabel, olabel[, w=one(W)])`

`add_arc!(fst, srcdest::Pair, ilabelolabel::Pair[, w=one(W)])`

状態 `src` から状態 `dest` へのアークを、入力ラベル `ilabel`、出力ラベル `olabel`、および重み `w` で追加します。代替表記では `Pair` を利用します。

`w` が提供されていない場合、これは `fst` の重みタイプ `W` に対してデフォルトで `one(W)` になります。
