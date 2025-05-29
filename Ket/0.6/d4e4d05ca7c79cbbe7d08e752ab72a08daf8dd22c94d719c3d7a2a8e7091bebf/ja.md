```
symmetric_isometry(dim::Integer, n::Integer)
```

`dim`次元空間の`n`コピーの対称部分空間をエンコードする等距離写像を計算します。具体的には、次元`binomial(n + dim -1, dim -1)`のベクトル空間を次元`dim^n`のベクトル空間の対称部分空間の対称部分空間にマッピングします。

参考文献: [Watrous' book](https://cs.uwaterloo.ca/~watrous/TQI/), Sec. 7.1.1
