```
find_oscillation_peak(psd, freqs; min_freq=5.0/1000.0, max_freq=50.0/1000.0, min_prominence_ratio=0.1)
```

パワースペクトル密度における支配的な振動ピークを見つけます。

# 引数

  * `psd::AbstractVector`: パワースペクトル密度の値
  * `freqs::AbstractVector`: 周波数の値
  * `min_freq::Real=5.0/1000.0`: 考慮する最小周波数
  * `max_freq::Real=50.0/1000.0`: 考慮する最大周波数
  * `min_prominence_ratio::Real=0.1`: 最大PSDの割合としての最小ピークの顕著性

# 戻り値

  * 最も顕著なピークの周波数、または有意なピークが見つからない場合はNaN

# 注意事項

  * ロバスト性のためにピークの顕著性を使用
  * 最小顕著性閾値でピークをフィルタリング
  * 条件を満たすピークがない場合はNaNを返す
