```
Percentile(x)
```

`x`は絶対値ではなく[パーセンタイル](https://en.wikipedia.org/wiki/Percentile)として解釈されるべきです。例えば、

  * `canny(img, 1.4, (80, 20))`はエッジの大きさ画像に対して絶対的な閾値を使用します
  * `canny(img, 1.4, (Percentile(80), Percentile(20)))`はエッジの大きさ画像のパーセンタイルを閾値として使用します
