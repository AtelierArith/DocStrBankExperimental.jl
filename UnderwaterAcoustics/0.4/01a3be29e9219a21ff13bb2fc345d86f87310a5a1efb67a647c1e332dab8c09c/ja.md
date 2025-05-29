```
soundspeed(temperature=27, salinity=35, depth=0; γ=0, cₐ=340, ρᵣ=1000)
```

水中の音速をm/sで計算します。与えられた条件は以下の通りです：

  * 水の`temperature`（温度）: °C
  * `salinity`（塩分）: ppt
  * `depth`（深さ）: メートル
  * 空隙率（`γ`）: 泡のある水
  * 気体中の音速（`cₐ`）: `γ` > 0 の場合
  * 水の密度と気体の密度の比（`ρᵣ`）: `γ` > 0 の場合

実装はMackenzie (1981)、Wood (1964)、およびBuckingham (1997)に基づいています。
