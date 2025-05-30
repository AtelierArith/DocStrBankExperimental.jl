```
colorsigned()
colorsigned(colorneg, colorpos) -> f
colorsigned(colorneg, colorcenter, colorpos) -> f
```

負の値（範囲[-1,0]）を`colorneg`と`colorcenter`の間の線形カラーマップに、正の値（範囲[0,1]）を`colorcenter`と`colorpos`の間の線形カラーマップにマッピングする関数を定義します。

デフォルトの色は次のとおりです：

  * `colorcenter`: 白
  * `colorneg`: 緑1
  * `colorpos`: マゼンタ

参照：[`scalesigned`](@ref)。
