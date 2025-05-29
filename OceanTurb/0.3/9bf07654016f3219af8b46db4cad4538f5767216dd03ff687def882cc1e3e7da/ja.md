```
relative_error(c, d, p=2)
```

`c`と`d`の相対誤差をノルム`p`で計算します。定義は次の通りです。

$$
\beq
\mathrm{rel \, error} = \frac{\left ( int_{-L}^0 (c-d)^p \, \mathrm{d} z \right )^(1/p)}
                             {\left ( int_{-L}^0 d^p \, \mathrm{d} z \right )^(1/p)}
\eeq
$$
