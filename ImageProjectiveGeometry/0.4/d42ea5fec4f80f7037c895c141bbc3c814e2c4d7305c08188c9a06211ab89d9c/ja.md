briefcoords - パッチ内でBRIEF記述子のサンプリング座標を計算します。

```
Usage:  rc = briefcoords(S, nPairs, UorG; disp=false)

Arguments:  S - パッチサイズを指定する奇数整数 (S x S)。
       nPairs - 必要な点ペアの数。通常、これは2の累乗であり、
                128、256、512など、記述子値をビット文字列に
                パッキングするために使用されます。
         UorG - パッチ内で形成される点ペアの分布が均一か
                ガウス分布かを示す文字 'U' または 'G'。
         disp - 点ペアのプロットを表示するかどうかを示す
                オプションのブールフラグ。

Returns:   rc - 整数の[2 x 2*nPairs]配列 (行; 列) 座標で、
                すべての値は -(S-1)/2..(S-1)/2 の範囲内です。
                各連続する列のペアは、画像のグレイ値を
                お互いに比較するための点のペアを提供することを
                意図しており、ある中心特徴位置の周りの
                パッチのBRIEF記述子を形成します。
```

点ペアのガウス分布の使用は、Calonderらが元の論文で提案したアプローチに対応しています。ただし、小さなパッチと多数のペアリングの場合、繰り返しペアリングが発生し、最終的な記述子の自由度が減少することに注意してください。均一に分布したオプションは繰り返しペアリングを生じないため、小さなパッチサイズには好ましいオプションです。

See also: grey2lbp(), grey2lbp!()
