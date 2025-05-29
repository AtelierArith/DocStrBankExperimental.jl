```
scale(r::ParamRange)
```

`ParamRange`オブジェクト`r`に関連付けられたスケールを返します。可能な返り値は、`:none`（`NominalRange`の場合）、`:linear`、`:log`、`:log10`、`:log2`、または`:custom`（`r.scale`が呼び出し可能なオブジェクトの場合）です。
