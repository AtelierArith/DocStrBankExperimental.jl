```
gamma_inc_cf(a, x, ind)
```

$$
P(a,x)
$$

を連分数展開によって計算します：

$$
R(a,x) \cdot \cfrac{1}{1-\cfrac{z}{a+1+\cfrac{z}{a+2-\cfrac{(a+1)z}{a+3+\cfrac{2z}{a+4-\cfrac{(a+2)z}{a+5+\cfrac{3z}{a+6-\ddots}}}}}}}
$$

`1 <= a <= BIG` および `x < x0` の場合に使用されます。

外部リンク: [DLMF 8.9.2](https://dlmf.nist.gov/8.9.2)

関連項目: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
