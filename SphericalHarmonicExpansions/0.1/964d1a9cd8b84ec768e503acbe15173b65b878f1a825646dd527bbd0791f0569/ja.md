```
translation(C::SphericalHarmonicCoefficients,v::Array{Float64,1})
```

*説明:* 係数の翻訳: vによる展開点のシフト

*入力:*

  * `C`  - 係数
  * `v`  - シフトベクトル (length(v) = 3)

*出力:*

  * `cT` - 翻訳された係数、タイプ: SphericalHarmonicCoefficients (cT.R = C.R, cT.solid = C.solid)

```
