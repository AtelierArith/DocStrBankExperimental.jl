```
modify_results!(mod::FuelPrice, config, data)
```

  * 各燃料タイプの各市場地域のクリアリング価格を計算します。

      * 地域内の最も安い燃料価格ステップの `cons_fuel_sold` のシャドウ価格に最も安い燃料価格を加えたもの
      * それを `fuel_markets.clearing_price` 列に追加します
      * `gen.fuel_price` 列をクリアリング価格（`heat_rate` 列で乗算）を使用するように更新します
