```
GrB_eWiseAdd(C, mask, accum, op, A, B, desc)
```

要素ごとの行列およびベクトル操作のための一般的なメソッド：集合の和を使用。

`GrB_eWiseAdd` は `C<Mask> = accum (C, A + B)` を計算します。ここで、2つの行列（または2つのベクトル）の要素のペアが対ごとに「加算」されます。「加算」演算子は任意の二項演算子にすることができます。プラス演算子を使用すると、これは従来の線形代数における行列の加算と同じです。結果 T = A + B のパターンは A と B の集合の和です。和の外にあるエントリは計算されません。つまり、A(i, j) と B(i, j) の両方が A と B のパターンに存在する場合、T(i, j) = A(i, j) "+" B(i, j) となります。A(i, j) のみが存在する場合、T(i, j) = A(i, j) となり、"+" 演算子は使用されません。同様に、B のパターンに B(i, j) のみが存在し、A のパターンに A(i, j) が存在しない場合、T(i, j) = B(i, j) となります。半環の場合、乗算演算子は半環の加算演算子です。
