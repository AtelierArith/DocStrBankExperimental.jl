```
get_model_violation(aces_data::ACESData; projected::Bool = false)
```

`aces_data`に保存されたノイズ推定に対応する一般化残差平方和のノイズモデル違反zスコアを返します。`projected`が`true`の場合は、`aces_data`に保存された設計を考慮して、投影ゲート固有値を用いて計算します。
