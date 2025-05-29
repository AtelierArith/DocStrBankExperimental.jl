```
time2freq(t)
```

は、ナイキスト基準に従って時間領域ベクトルを周波数のベクトルに変換します。Johanna Vannesjoのtime2freqメソッドの一部です: https://github.com/MRI-gradient/GIRF/blob/main/utils/time2freq.m

# 引数

  * `t` - 入力時間ベクトル

# 出力

  * `f` - 計算された周波数軸、[length(t)]のベクトル
  * `df` - 周波数分解能
  * `f_max` - 完全な周波数範囲。周波数軸の範囲は[-f*max/2, f*max/2]です。
