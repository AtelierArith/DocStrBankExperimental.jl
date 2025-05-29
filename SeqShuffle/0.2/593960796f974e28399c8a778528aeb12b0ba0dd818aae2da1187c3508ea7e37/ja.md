```
seq_shuffle(seq::String; k=2, seed=nothing)
```

入力文字列をシャッフルしてk-merの頻度を保持します。

入力:

  * `seq`: 文字列
  * `k`: 整数; k-merの頻度
  * `seed`: (整数) ランダム数生成のためのシード

出力:     入力文字列`seq`のシャッフルされたバージョン
