```
SmoothRect(F, tstart, tr, duration)
```

滑らかな矩形励振信号を定義する構造体

**フィールド**

  * `F::Real`: 力の振幅 [N]
  * `tstart::Real`: 励振の開始時間 [s]
  * `duration::Real`: 励振の持続時間 [s]
  * `trise::Real`: 0からFへの上昇時間 [s]

*注: `SmoothRect`は実際にはカスタムTukeyウィンドウであり、係数αはユーザーによって与えられた`trise`を満たすように計算されます*
