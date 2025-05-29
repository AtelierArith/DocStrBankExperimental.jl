```
absolute_error(c, d, p=2)
```

`c`と`d`の間の絶対誤差をノルム`p`で計算します。定義は次の通りです。

$$
\mathrm{abs \, error} = \left ( L^{-1} \int_{-L}^0 |c-d|^p \, \mathrm{d} z \right )^(1/p)
$$

。

`c`と`d`が異なるグリッドにある場合、`d`は`c`と同じグリッドに補間されます。
