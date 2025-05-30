```
RandomCascade(paddingmode::String = "zeros")
```

ランダムカスケード多重フラクタルウェーブレットサロゲート (Paluš, 2008)[^Paluš2008]。

入力信号の長さが2の累乗でない場合、サロゲートが構築される前に信号をパディングする必要があります。`paddingmode`は信号のパディング方法を決定します。現在サポートされているパディングモード: `"zeros"`。最終的なサロゲート（パディングされた信号から構築されたもの）は、元の信号の長さに合わせてサブセットされます。

ランダムカスケードサロゲートは、入力時系列の多重フラクタル特性を保持します。つまり、二進スケール間の相互作用や非線形依存性[^Paluš2008]。

[^Paluš2008]: Paluš, Milan (2008). Bootstrapping Multifractals: Surrogate Data from Random Cascades on Wavelet Dyadic Trees. Physical Review Letters, 101(13), 134101–. doi:10.1103/PhysRevLett.101.134101
