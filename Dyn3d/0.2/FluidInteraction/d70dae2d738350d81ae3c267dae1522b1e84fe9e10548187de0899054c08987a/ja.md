```
DetermineNP(nbody::Int, Δx)
```

この関数を `GenerateBodyGrid` を実行する前に実行して、1次元ボディ上の希望するポイント数を満たすために2次元ボディ上のポイント数を決定します。

np = (# of points on 1d plate - 1)*4+1. したがって、np=201は51ポイント（1ボディ）、np=101は26ポイント（2ボディ）、np=49は13ポイント（4ボディ）、np=25は7ポイント（8ボディ）などです。
