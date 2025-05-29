```
concatenate(S11a,S12a,S21a,S22a,S11b,S12b,S21b,S22b)
concatenate(S1::ScatterMatrix,S2::ScatterMatrix)
concatenate(Sin::Array{ScatterMatrix,1})
```

結合層のための全散乱行列を連結によって計算します

# 引数

  * `S11a` : 最初の散乱行列のS11成分
  * `S12a` : 最初の散乱行列のS12成分
  * `S21a` : 最初の散乱行列のS21成分
  * `S22a` : 最初の散乱行列のS22成分
  * `S11b` : 2番目の散乱行列のS11成分
  * `S12b` : 2番目の散乱行列のS12成分
  * `S21b` : 2番目の散乱行列のS21成分
  * `S22b` : 2番目の散乱行列のS22成分
  * `S1` : 最初の散乱行列
  * `S2` : 2番目の散乱行列
  * `Sin` : 散乱行列の配列（連鎖連結）

# 出力

  * `Sout` : 全散乱行列
