```
Windows3(y, t, v, n=length(y)÷8, noverlap=-1, window_func=rect)
```

noverlap = -1 は noverlap を n/2 に設定します

#引数:

  * `y`: 信号
  * `t`: 時間ベクトル
  * `v`: 補助ベクトル
  * `n`: ウィンドウあたりのデータポイント数
  * `noverlap`: ウィンドウ間のオーバーラップ
  * `window_func`: ウィンドウに適用する関数
