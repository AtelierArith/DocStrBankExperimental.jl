```
distancetrace_spaceneeded(n, p; bits=64) = Base.format_bytes(binomial(n,2) * p * bits)
```

スペクトル残差トレースを保存するのに必要なメモリはどのくらいですか？

引数:

  * n: サンプル数
  * p: パーティション/コンポーネントの数
