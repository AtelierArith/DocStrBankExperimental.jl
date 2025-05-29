```
K, Ti, Td = parallel2standard(Kp, Ki, Kd)
```

パラメータを「並列」形式 $K_p + K_i/s + K_d s$ から「標準」形式 DiscretePID で使用される $K(1 + 1/(T_i s) + T_d s)$ に変換します。

3つの引数または同じ順序の3つの要素を持つ配列を提供できます。
