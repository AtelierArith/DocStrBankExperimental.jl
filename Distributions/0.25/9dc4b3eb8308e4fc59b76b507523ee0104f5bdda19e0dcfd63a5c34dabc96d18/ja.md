```
Arcsine(a,b)
```

*アークサイン分布*は確率密度関数を持ちます

$$
f(x) = \frac{1}{\pi \sqrt{(x - a) (b - x)}}, \quad x \in [a, b]
$$

```julia
Arcsine()        # サポート [0, 1] のアークサイン分布
Arcsine(b)       # サポート [0, b] のアークサイン分布
Arcsine(a, b)    # サポート [a, b] のアークサイン分布

params(d)        # パラメータを取得します、すなわち (a, b)
minimum(d)       # 下限を取得します、すなわち a
maximum(d)       # 上限を取得します、すなわち b
location(d)      # 左端を取得します、すなわち a
scale(d)         # サポートの範囲を取得します、すなわち b - a
```

外部リンク

  * [アークサイン分布 - Wikipedia](http://en.wikipedia.org/wiki/Arcsine_distribution)

`Arcsine(a, b, check_args=false)`を使用して引数チェックをバイパスします。
