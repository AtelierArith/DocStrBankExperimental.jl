```
blockerr(lengt, nsegmentts; <keyword arguments>)
```

データをセグメントに分割するためのブロッカーコード

...

# 引数

  * `lengt::Int64`: 時系列の入力長
  * `nsegments::Int64`: セグメントの数
  * `overlap::Float64 = 0.0`: セグメント間のオーバーラップの割合、0.0から1.0の間

...

...

# 出力

  * `seq::Vector{Int64}`: 各セグメントの開始インデックス
  * `seg_len::Int64`: セグメントの長さ
  * `ov::Float64`: 実際に得られたオーバーラップ (≈`overlap`, 上記)

...
