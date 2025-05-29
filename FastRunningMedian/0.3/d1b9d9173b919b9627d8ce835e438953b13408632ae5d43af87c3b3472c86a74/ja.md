```
median(mf::MedianFilter; nan=:include)
```

`mf`の現在の中央値を決定します。

## NaNの取り扱い

デフォルトでは、フィルター内のNaN値は結果をNaNにします。

キーワード引数`nan = :ignore`を使用すると、NaN値を無視して残りの値の中央値を計算します。すべてがNaNの場合、中央値は常にNaNになります。

## 実装

MedianFilter内の要素数が奇数の場合、low*heapは常にhigh*heapよりも1つ大きくなります。したがって、low_heapのトップ要素が中央値になります。

MedianFilter内の要素数が偶数の場合、両方のヒープは同じサイズであり、中央値は両方のトップ要素の平均になります。
