```
J = imhdome(I::GMTimage{<:UInt8, 2}, H; conn=4)::GMTimage
```

### 引数

  * `I::GMTimage{<:UInt8, 2}`: 入力画像。
  * `H`: フィリングマスクhdomeの下の高さ; 0以上でなければならない（Leptonica pixHDome() ドキュメントの言葉）

### キーワード引数

  * `conn::Int=4`: I内の領域の最大値を特定するために使用される接続性値（4または8）。デフォルトは4です。

### 戻り値

`I`と同じ型の新しい$GMTimage$。
