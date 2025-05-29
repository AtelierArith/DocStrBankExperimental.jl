derivative5 - 5タップ1次および2次離散導関数

この関数は、FaridとSimoncelliによって与えられた5タップ係数を使用して画像の1次および2次導関数を計算します。結果は、垂直または水平方向以外の角度でのエッジに対して、単純な勾配関数よりもはるかに正確です。これにより、勾配方向の推定が大幅に改善されます。極めて高い精度を求める場合は、derivative7()の使用を検討してください。

```
Usage:  (gx, gy, gxx, gyy, gxy) = derivative5(img, derivative_specifiers)

Arguments:
                     img - 導関数を計算するための画像。 ::Array{T,2}
   derivative specifiers - 任意の順序で "x", "y", "xx", "yy" または "xy" のいずれかの文字列のタプル
                           計算された出力引数の順序は、導関数指定子文字列の順序に一致します。
Returns:
 関数は要求された導関数を返します。これには以下が含まれます：
    gx, gy   - xおよびyの1次導関数
    gxx, gyy - xおよびyの2次導関数
    gxy      - xの1次導関数のyにおける1次導関数

 Examples:
   xおよびyの1次導関数を計算するだけ
   (gx, gy) = derivative5(img, ("x", "y"))

   xの2次導関数、yの1次導関数、およびyの2次導関数を計算する
   (gxx, gy, gyy) = derivative5(img, ("xx", "y", "yy"))
```

See also: derivative7()
