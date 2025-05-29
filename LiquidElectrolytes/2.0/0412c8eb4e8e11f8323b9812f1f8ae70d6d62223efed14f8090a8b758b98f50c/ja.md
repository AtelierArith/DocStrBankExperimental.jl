```
currents(result,ispec; electrode)
```

種 `ispec` の電極電流のベクトル。電極は次のいずれかです：

  * `:bulk`: バルク境界条件での電流を計算
  * `:we`: 電極界面での電流を計算
  * `:reaction`: 反応項からの電流を計算
