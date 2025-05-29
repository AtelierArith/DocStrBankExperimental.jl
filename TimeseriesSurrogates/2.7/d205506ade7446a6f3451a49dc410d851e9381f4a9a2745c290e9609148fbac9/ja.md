```
RandomFourier(phases = true)
```

信号のフーリエ成分を何らかの方法でランダム化するサロゲートです。`phases==true` の場合、位相がランダム化され、それ以外の場合は振幅がランダム化されます。`FT` は `RandomFourier` のエイリアスです。

ランダムフーリエ位相サロゲート[^Theiler1991]は、元の信号の自己相関関数またはパワースペクトルを保持します。ランダムフーリエ振幅サロゲートは、平均と自己相関関数を保持しますが、元の分散は保持しません。ランダム振幅サロゲートは文献では一般的ではありませんが、便宜のために提供されています。

ランダム位相サロゲートは、元の信号が線形ガウス過程によって生成されたという帰無仮説をテストするために使用できます[^Theiler1991]。

[^Theiler1991]: J. Theiler, S. Eubank, A. Longtin, B. Galdrikian, J. Farmer, Testing for nonlinearity in time series: The method of surrogate data, Physica D 58 (1–4) (1992) 77–94.
