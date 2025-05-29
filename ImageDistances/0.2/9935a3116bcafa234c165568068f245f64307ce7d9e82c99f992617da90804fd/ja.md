```
NCC <: Metric
ncc(x, y)
```

正規化相互相関(ncc)は `dot(mean(x),mean(y))/(norm(mean(x))*norm(mean(y)))` によって計算されます。

$$
\frac{<\bar{x}, \bar{y}>}{||\bar{x}||*||\bar{y}||}
$$

!!! info
    NCCはメトリックではありません。なぜなら `ncc(x, x) == 1.0` だからです。

