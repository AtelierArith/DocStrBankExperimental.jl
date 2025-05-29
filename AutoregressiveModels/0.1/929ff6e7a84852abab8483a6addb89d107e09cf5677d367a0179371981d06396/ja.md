```
ARMAProcess(ars, mas, intercept=nothing)
```

自己回帰移動平均過程 $y_t$ を次のように定義します

$$
\left(1-\sum_{i=1}^p \rho_i L^i\right) = c + \left(1-\sum_{i=1}^q \varphi_i L^i\right) \varepsilon_t
$$

ここで、$\{\rho_i\}_i$, $\{\varphi_i\}_i$ および $c$ はそれぞれ `mas`, `ars` および `intercept` で指定されます; $L$ はラグ演算子です。移動平均項に関連する*負*の符号に注意してください。
