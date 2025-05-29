```
Percentile(x)
```

`x`は絶対値ではなく[パーセンタイル](https://en.wikipedia.org/wiki/Percentile)として解釈されるべきであることを示します。例えば、

  * `detect_edges(img, Canny(high = 80, low = 20))`はエッジの大きさに対して絶対的な閾値を使用します
  * `detect_edges(img, Canny(high = Percentile(80), low = Percentile(20)))`はエッジの大きさ画像のパーセンタイルを閾値として使用します
