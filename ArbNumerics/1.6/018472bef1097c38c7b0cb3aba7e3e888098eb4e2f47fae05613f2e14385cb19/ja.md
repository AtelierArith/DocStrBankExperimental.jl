```
ArbFloat(x)
ArbFloat(x; [bits])
ArbFloat(x; [digits [, base=10]])
```

  * ArbFloat(x) == ArbFloat(x, bits=workingprecision(ArbFloat))
  * ArbFloat(x, digits=digits, base=2) == ArbFloat(x, bits=digits)
  * ArbFloat(x, digits=digits, base=10) == ArbFloat(x, digits=digits)

ArbFloatsは、構築時に特定の精度が設定された任意精度のバイナリ浮動小数点数です。

ArbFloatの精度は、>= 24ビットまたは>= 8桁でなければなりません。

負のゼロ、符号なしの無限大、異なるペイロードを持つNaNはサポートされていません。

参照: [`ArbReal`](@ref), [`ArbComplex`](@ref), [`workingprecision`](@ref), [`displayprecision`](@ref)
