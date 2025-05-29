```julia
struct Zone
```

市場ゾーンを定義する型です。`Zone`は番号で識別されます。他のフィールドにはゾーンのサービス要件が含まれています。要件は基準電力100MWを前提として`pu`で示されます。

フィールド:

  * `number::Int64`: ゾーン番号
  * `regulation::Float64`: ゾーンの調整要件 (pu)
  * `operating_reserve::Float64`: ゾーンの運用予備要件 (調整 + 回転 + 補助) (pu)
  * `good_utility::Float64`: ゾーンの良好なユーティリティプラクティス要件 (調整 + 回転) (pu)
