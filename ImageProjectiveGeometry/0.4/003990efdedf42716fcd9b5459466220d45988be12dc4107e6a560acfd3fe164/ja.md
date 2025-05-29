derivative3 - 3タップ離散微分フィルタ

この関数は、FaridとSimoncelliによって与えられた3タップ係数を使用して画像の1次微分を計算します。結果は、垂直または水平方向以外の角度にあるエッジに対して、単純な勾配関数よりもはるかに正確です。これにより、勾配の方向推定が大幅に改善されます。極端な精度を求める場合は、derivative7()の使用を検討してください。

```
Usage:  (gx, gy) = derivative3(img, derivative specifiers)

Arguments:
                     img - 微分を計算する画像。 ::Array{T,2}
   derivative specifiers - "x"または"y"のいずれかの文字列のタプル
                           これらは任意の順序で指定でき、
                           計算された出力引数の順序は
                           微分指定子文字列の順序に一致します。
Returns:
 関数は要求された微分を返します。これには以下が含まれます：
    gx, gy   -  xおよびyの1次微分

 Example:
   xおよびyの1次微分を計算
   (gx, gy) = derivative3(img, ("x", "y"))
```

See also: derivative5(), derivative7()
