```
SurvivalCopula{P}
```

フィールド:

```
- C::bicopula
```

コンストラクタ

```
SurvivalCopula(C)
```

二変量サバイバルコピュラは次のように定義されます

$$
\overbar{C}(u_1,u_2) = C(u_1, u_2) + u_1 + u_2 - 1
$$

ここで、$C(u_1, u_2)$は私たちが知っているコピュラです。

参考文献:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
