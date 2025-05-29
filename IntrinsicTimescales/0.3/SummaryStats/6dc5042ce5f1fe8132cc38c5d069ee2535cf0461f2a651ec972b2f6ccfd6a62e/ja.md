```
prepare_lombscargle(times, data, nanmask)
```

Lomb-Scargle パワースペクトル計算のために、欠損値を処理してデータを準備します。

# 引数

  * `times`: 時間ポイントベクトル
  * `data`: 時系列データ（NaN を含む可能性があります）
  * `nanmask`: NaN の位置を示すブールマスク

# 戻り値

  * `valid_times`: NaN 値が削除された時間ポイント
  * `valid_data`: NaN 値が削除されたデータポイント
  * `frequency_grid`: 分析のために提案された周波数グリッド
