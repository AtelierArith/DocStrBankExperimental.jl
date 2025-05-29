```
N = remezord(Wp, Ws, Rp, Rs)
```

ローパスデジタルフィルタの場合の次数推定は、[^^Rabiner]の方程式と係数に基づいています。元の方程式は最小フィルタ長を返しましたが、この実装は次数（N=L-1）を返します。`Wp`と`Ws`は正規化された通過帯域および阻止帯域の周波数で、`Rp`は通過帯域のリップルを示し、`Rs`は阻止帯域の減衰（線形）です。

注意：Nの値は初期の近似値です。過小評価された場合は、設計仕様を満たすまで次数を増やす必要があります。

[^Rabiner]: Herrmann, O., Lawrence R. Rabiner, and D. S. K. Chan. "Practical

design rules for optimum finite impulse response lowpass digital filters." Bell System  Technical Journal 52.6 (1973): 769-799.
