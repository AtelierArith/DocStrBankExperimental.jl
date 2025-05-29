histtruncate - 画像ヒストグラムの端を切り詰めます。

関数は、画像ヒストグラムの下端と上端の指定された割合を切り詰めます。

この操作により、灰色レベルがヒストグラムの主要部分に分配されるようになります。これは、たとえば、画像に非常に明るい値がいくつかあり、再スケーリング後に画像全体が暗くなるという問題を解決します。

```
Usage:
1)   newimg = histtruncate(img, lHistCut, uHistCut)
2)   newimg = histtruncate(img, HistCut)

Arguments:
 Usage 1)
   img         -  処理する画像。
   lHistCut    -  ヒストグラムの下端を飽和させる割合。
   uHistCut    -  ヒストグラムの上端を飽和させる割合。省略または空の場合は
                  lHistCutの値がデフォルトとなります。
 Usage 2)
   HistCut     -  ヒストグラムの上端と下端を切り詰める割合。

Returns:
   newimg      -  指定されたヒストグラムの割合値でクリップされた値を持つ画像。
                  入力画像がカラーの場合、明度値はクリップされ、範囲
                  0-1にストレッチされます。入力画像がグレースケールの場合、
                  ストレッチは適用されません。これを達成するために
                  normalise()を使用することをお勧めします。
```

See also: normalise
