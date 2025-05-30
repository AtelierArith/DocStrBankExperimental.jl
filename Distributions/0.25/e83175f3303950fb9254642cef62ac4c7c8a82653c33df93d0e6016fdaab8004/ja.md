```
TriangularDist(a,b,c)
```

*三角分布*は、下限 `a`、上限 `b`、およびモード `c` を持ち、確率密度関数は次のようになります。

$$
f(x; a, b, c)= \begin{cases}
        0 & \mathrm{for\ } x < a, \\
        \frac{2(x-a)}{(b-a)(c-a)} & \mathrm{for\ } a \le x \leq c, \\[4pt]
        \frac{2(b-x)}{(b-a)(b-c)} & \mathrm{for\ } c < x \le b, \\[4pt]
        0 & \mathrm{for\ } b < x,
        \end{cases}
$$

```julia
TriangularDist(a, b)        # 下限 a、上限 b、およびモード (a+b)/2 の三角分布
TriangularDist(a, b, c)     # 下限 a、上限 b、およびモード c の三角分布

params(d)       # パラメータを取得します。すなわち (a, b, c)
minimum(d)      # 下限を取得します。すなわち a
maximum(d)      # 上限を取得します。すなわち b
mode(d)         # モードを取得します。すなわち c
```

外部リンク

  * [三角分布 - Wikipedia](http://en.wikipedia.org/wiki/Triangular_distribution)
