```julia
interp1(x, y, xi)

```

interp1は、ベクトルまたは配列xiの点での基になる関数Yの値yiを見つけるために補間します。xはベクトルでなければなりません。http://www.mathworks.co.jp/help/techdoc/ref/interp1.html

**パラメータ**

  * `x` : 入力ベクトル（時間軸）
  * `y` : x[n]での値
  * `xi`: 必要なベクトル

**戻り値**

  * `yi` : 補間されたベクトル
