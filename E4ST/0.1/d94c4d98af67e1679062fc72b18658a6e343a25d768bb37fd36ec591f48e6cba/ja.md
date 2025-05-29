```
modify_model!(mod::FuelPrice, config, data, model)
```

  * `data[:fuel_markets]`を各燃料市場を追跡するために保持します
  * 変数`fuel_sold[fuel_price_idx,  yr_idx, hr_idx]`を追加します：各価格ステップでの各時間間隔における総燃料販売量
  * 式`fuel_used[fuel_market_idx, yr_idx, hr_idx]`を追加します：各市場地域における発電機による総燃料使用量
  * 式`fuel_price_obj[fuel_market_idx, yr_idx, hr_idx]`を追加します：目的に追加される燃料の総コスト。
  * 制約`cons_fuel_sold[fuel_price_idx, yr_idx]`を追加します：各年の総`fuel_sold`を年間数量以下に制約します
  * 制約`cons_fuel_bal[fuel_market_idx, yr_idx, hr_idx]`を追加します：各市場地域で販売される燃料の量が各市場地域で使用される燃料の量と等しくなるように制約します。

`fuel_sold`と`fuel_used`は、これらの制約で一緒に使用される変数間のサイズの違いを減らすためにfp_scalarを使用してスケールダウンされます。 これにより、目的スカラーが高いときにシャドウプライスが0に丸められることがある問題を防ぎます。
