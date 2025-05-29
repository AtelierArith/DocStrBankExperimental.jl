```
format(x,fs,ch)
```

信号 `x` のサンプリングレート (`fs`) とチャンネル `ch` を効率的に変換します。これは、冗長な計算を避けるために `tosamplerate` と `tochannels` の最適な順序を選択します。
