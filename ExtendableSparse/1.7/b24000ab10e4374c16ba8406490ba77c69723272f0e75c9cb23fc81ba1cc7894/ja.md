```
 BlockPreconBuilder(;precs=UMFPACKPreconBuilder(),  
                     partitioning = A -> [1:size(A,1)]
```

未知数の分割から左ブロックヤコビ前処理器を構築する呼び出し可能なオブジェクトを返します。

  * `partitioning(A)` は、行列のパーティションのインデックスを記述するAbstractVectorsのベクトルを返す必要があります。行列のサイズが `n x n` の場合、例えば、分割は `[ 1:n÷2, (n÷2+1):n]` または [ 1:2:n, 2:2:n] である可能性があります。
  * `precs(A,p)` は、行列ブロックの左前処理器を返す必要があります。
