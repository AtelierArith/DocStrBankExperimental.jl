```julia
makeisolevels(func, levels, limits, colorbarticks)

```

funcで与えられたベクトルに基づいてlevels、limits、colorbarticsを更新します。

  * `limits[1]>limits[2]`の場合、`extrema(func)`で置き換えます。
  * levelsが数値の場合、limits内の長さlevels+2の線形範囲で置き換えます。
  * colorbarticksが`nothing`の場合、levelsで置き換え、結果にlimitsを追加します。それ以外の場合、数値であれば、対応する長さの線形範囲で置き換えます。
