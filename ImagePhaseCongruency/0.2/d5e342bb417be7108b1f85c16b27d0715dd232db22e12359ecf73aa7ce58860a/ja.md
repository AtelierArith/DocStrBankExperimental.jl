幾何級数を生成します。

フィルターバンクを指定するための幾何学的にスケーリングされた波長を生成するのに便利です。

```
Usage 1: s = geoseries(s1, mult, n)

Arguments:      s1 - シリーズの開始値。
              mult - 連続する値の間のスケーリングファクター。
                 n - シリーズ内の要素の希望数。

Usage 2: s = geoseries((s1, sn), n)

Arguments: (s1, sn) - シリーズ内の最初と最後の値を指定するタプル。
                  n - シリーズ内の要素の希望数。
```

例:

```
      s = geoseries(0.5, 2, 4)
      s =  [0.5000,    1.0000,    2.0000,    4.0000]
```

または、次のようにして同じ系列を取得します。

```
           s = geoseries((0.5, 4), 4)
```
