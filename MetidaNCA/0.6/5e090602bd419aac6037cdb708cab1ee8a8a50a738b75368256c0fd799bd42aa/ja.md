```
DoseTime(dose::D, time::T, tau::TAU) where D <: Number where T <: Number where TAU <: Number
```

投与設定。

  * `dose` - 投与量;
  * `time` - 投与時間;
  * `tau` - タウ (τ);

投与時間はデフォルトで0に設定されています。
