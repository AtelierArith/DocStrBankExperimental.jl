derivative7 - 7タップ1次および2次離散導関数

この関数は、FaridとSimoncelliによって与えられた7タップ係数を使用して、画像の1次および2次導関数を計算します。結果は、垂直または水平方向以外の角度にあるエッジに対して、単純な勾配関数よりもはるかに正確です。これにより、勾配方向の推定が大幅に改善されます。

```
Usage:  (gx, gy, gxx, gyy, gxy) = derivative7(img, derivative specifiers)

Arguments:
                      im - 導関数を計算する画像。 ::Array{T,2}
   derivative specifiers - 任意の順序で "x"、"y"、"xx"、"yy" または "xy" のいずれかの文字列のタプル
                           計算された出力引数の順序は、導関数指定子文字列の順序と一致します。
Returns:
 関数は要求された導関数を返します。これには次のものが含まれます：
    gx, gy   -  xおよびyの1次導関数
    gxx, gyy -  xおよびyの2次導関数
    gxy      -  xの1次導関数のyにおける1次導関数

 Examples:
   xおよびyの1次導関数を計算するだけ
   (gx, gy) = derivative7(img, ("x", "y"))

   xの2次導関数、yの1次導関数、およびyの2次導関数を計算する
   (gxx, gy, gyy) = derivative7(img, ("xx", "y", "yy"))
```

See also: derivative5()
