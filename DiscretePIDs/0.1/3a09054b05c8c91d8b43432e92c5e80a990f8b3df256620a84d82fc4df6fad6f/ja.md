```
K, Ti, Td, N = parallel2standard(Kp, Ki, Kd, Tf)
```

パラメータを「並列」形式から「標準」形式に変換します。並列形式は次のようになります：$K_p (br-y) + K_i (r-y)/s - K_d s y/(Tf s + 1)$

標準形式は、DiscretePIDで使用される形式です：$K (br-y + (r-y)/(T_i s) - T_d s y/(T_d / N s + 1))$

4つの引数を提供するか、同じ順序で4つの要素を持つ配列を提供できます。
