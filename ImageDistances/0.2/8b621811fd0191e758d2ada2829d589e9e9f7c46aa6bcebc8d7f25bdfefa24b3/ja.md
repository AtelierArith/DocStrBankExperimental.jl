```
ZNCC <: PreMetric
zncc(x, y)
```

ゼロ平均正規化相互相関（ZNCC）は `dot(x,y)/(norm(x)*norm(y))` によって計算されます：

$$
\frac{<\bar{x}, \bar{y}>}{||\bar{x}||*||\bar{y}||}
$$

ここで `x`/`y` はゼロ平均化されます。すなわち、`x := x - mean(x)` です。

!!! info
    ZNCC は `Metric` ではありません。なぜなら `zncc(x, x) == 1.0` だからです。入力配列のいずれかが全てゼロの場合、ZNCC は `NaN` を出力する可能性があります。


# 参考文献

[1] Nakhmani, Arie, and Allen Tannenbaum. "A new distance measure based on generalized image normalized cross-correlation for robust video tracking and image recognition." *Pattern recognition letters* 34.3 (2013): 315-321.
