```
SeisPOCS(in;<keyword arguments>)
```

凸集合への射影による地震記録の補間。

# 引数

  * `in`: 最大5次元の入力データ。時間は最初の次元にあります。
  * `p=1.` : 閾値処理のための指数（1はソフト閾値に相当し、高い数値はハード閾値に相当します）
  * `alpha=1` : 補完ステップのための戻し比率。ノイズのないデータには1を使用し、元のトレースのデノイジングには1未満を使用します。
  * `dt=0.001` : 時間軸に沿ったサンプリングレート（秒単位）
  * `fmax=99999.` : 処理する最大時間周波数。
  * `padt=2` : 時間軸のパディング、最初の次元。
  * `padx=1` : 空間軸のパディング。（次元2から5）。
  * `Niter=100` : 繰り返し回数
  * `alpha=1`
