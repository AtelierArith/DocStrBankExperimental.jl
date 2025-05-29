```
ArbComplex(x)
ArbComplex(x; [bits])
ArbComplex(x; [digits [, base=10]])

ArbComplex(re, im)
ArbComplex(re, im; [bits])
ArbComplex(re, im; [digits [, base=10]])
```

  * `ArbComplex`(re, im) == `ArbComplex`(re, im, bits=workingprecision(ArbComplex))
  * `ArbComplex`(re, im, digits=digits, base=2) == `ArbComplex`(re, im, bits=digits)
  * `ArbComplex`(re, im, digits=digits, base=10) == `ArbComplex`(re, im, digits=digits)

`ArbComplex`は、構築時に特定の精度が設定された任意精度の複素数バイナリ浮動小数点領域です。

`ArbComplex`の精度は、>= 24ビットまたは>= 8桁でなければなりません。

内部的に、`ArbComplex`は`ArbReal`のペアとして表現され、実部と虚部はそれぞれ中点と半径（区間の半幅）によって与えられる区間です。この表現は複素数上の*ボール*として機能します。`ArbComplex`を用いた計算は、真の数学的結果を含むことが保証された結果を生成します。結果の区間の幅に関しては事前の保証はありません。良い実践は、必要な結果の幅の精度よりも実質的に大きな精度を設定し、結果の半径を確認することです。

参照: [`ArbFloat`](@ref), [`ArbReal`](@ref), [`ball`](@ref), [`setball`](@ref), [`midpoint`](@ref), [`radius`](@ref)
