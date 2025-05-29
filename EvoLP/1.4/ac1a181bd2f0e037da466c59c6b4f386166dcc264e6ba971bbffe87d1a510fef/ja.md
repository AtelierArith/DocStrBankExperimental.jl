```
circle(x)
```

!!! warning "EvoLP 1.3から非推奨"
    このテスト関数は将来のメジャーリリースで**非推奨**になります。


**circle**関数は多目的テスト関数であり、次のように定義されます。

$$
f(x) = \begin{bmatrix}
        1 - r\cos(\theta) \\
        1 - r\sin(\theta)
        \end{bmatrix}
$$

ここで、$\theta=x_1$であり、$r$は次のように得られます。

$$
r = \frac{1}{2} + \frac{1}{2} \left(\frac{2x_2}{1+x_2^2}\right)
$$
