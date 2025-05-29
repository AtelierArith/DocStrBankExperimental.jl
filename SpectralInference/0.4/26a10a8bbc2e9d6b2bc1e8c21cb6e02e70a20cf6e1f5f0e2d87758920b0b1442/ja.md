```
distancematrix_spaceneeded(n, p; bits=64) = Base.format_bytes(binomial(n,2) * p * bits)
```

距離行列を格納するのに必要なメモリ

引数:

  * n: サンプルの数
