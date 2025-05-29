```
FlashSpecifications(;v,T,p,h,s,u,q)
```

一般的なフラッシュのための2つの仕様を保持する構造体です。キーワード引数は以下の意味を持ちます：

  * `T`: 温度
  * `v`: 総体積
  * `p`: 圧力
  * `h`: エンタルピー
  * `s`: エントロピー
  * `u`: 内部エネルギー
  * `q`: 蒸気分率

## 例：

```
specs = FlashSpecifications(p = 101325,T = 298.15) #PTフラッシュ
specs = FlashSpecifications(Clapeyron.pressure,101325,Clapeyron.temperature,298.15) #同等
```
