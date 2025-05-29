```
ArbReal(x)
ArbReal(x; [bits])
ArbReal(x; [digits [, base=10]])
```

  * `ArbReal`(x) == `ArbReal`(x, bits=workingprecision(ArbReal))
  * `ArbReal`(x, digits=digits, base=2) == `ArbReal`(x, bits=digits)
  * `ArbReal`(x, digits=digits, base=10) == `ArbReal`(x, digits=digits)

ArbRealsは、構築時に特定の精度が設定された任意精度のバイナリ浮動小数点領域です。

`ArbReal`の精度は、>= 24ビットまたは>= 8桁でなければなりません。

内部的に、`ArbReal`はその中点と半径（区間の半幅）によって与えられる区間を表します。この表現は実数上の*ボール*として機能します。 `ArbReals`を用いた計算は、真の数学的結果を含むことが保証された結果を生成します。結果として得られる区間の幅に関しては事前の保証はありません。良い実践としては、必要な結果の幅の精度よりも実質的に大きな精度を設定し、結果の半径を確認することです。

参照: [`ArbFloat`](@ref), [`ArbComplex`](@ref), [`ball`](@ref), [`setball`](@ref), [`midpoint`](@ref), [`radius`](@ref)
