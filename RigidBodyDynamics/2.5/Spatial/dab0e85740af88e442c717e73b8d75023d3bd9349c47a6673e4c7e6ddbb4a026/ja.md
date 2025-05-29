```julia
struct Wrench{T}
```

レンチは力のシステムを表します。

フレーム $i$ で表現されたレンチ $w^i$ は次のように定義されます。

$$
w^{i} =
\left(\begin{array}{c}
\tau^{i}\\
f^{i}
\end{array}\right) =
\sum_{j}\left(\begin{array}{c}
r_{j}^{i}\times f_{j}^{i}\\
f_{j}^{i}
\end{array}\right)
$$

ここで、$f_{j}^{i}$ はフレーム $i$ で表現された力であり、位置 $r_{j}^{i}$ で作用します。$\tau^i$ は合計トルクであり、$f^i$ は合計力です。
