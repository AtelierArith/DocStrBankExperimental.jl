```
Disk{T}() where {T}
```

トッパハットディスクの幾何学モデル、すなわち強度プロファイル

$$
    I(x,y) = \begin{cases} \pi^{-1} & x^2+y^2 < 1 \\ 0 & x^2+y^2 \geq 0 \end{cases}
$$

すなわち、単位半径および単位フラックスのディスク。

デフォルトでは、Tが指定されていない場合、`Disk`は`Float64`にデフォルト設定されます。
