```
SymmetricTensor(frame, bls, bln, dats, sqr)
```

対称テンソルを構築します。

# 引数

  * `frame::ArrayNArrays{T,N}`: 生データ。
  * `bls::Int`: 通常のブロックのサイズ（各方向で同じ）。
  * `bln::Int`: 各方向の最大ブロック数。
  * `dats::Int`: 保存されるデータのサイズ（各方向で同じ）。
  * `sqr::Bool`: すべてのブロックが正方形であるかどうか（N-正方形）。
