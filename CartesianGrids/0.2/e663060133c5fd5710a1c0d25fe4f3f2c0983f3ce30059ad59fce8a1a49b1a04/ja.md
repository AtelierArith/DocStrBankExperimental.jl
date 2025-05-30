```
test_cputime(nx,ny,nthreads_max;[nsamp=1][,testtype=:laplacian][,kwargs]) -> Float64, Float64
```

与えられたグリッドサイズ `nx` x `ny` と指定された最大スレッド数 `nthreads_max` を使用して、サンプルのFFTベースの問題を評価します。計算時間の平均と標準偏差を返します。オプションの引数 `nsamp` を使用して、複数のサンプルにわたる平均タイミングを実行できます。テストタイプはオプションの引数 `testtype` で指定されます。デフォルトのテストはラプラス演算子の逆行列（`:laplacian`）です。他のオプションは `:intfact` と `:helmholtz` です。
