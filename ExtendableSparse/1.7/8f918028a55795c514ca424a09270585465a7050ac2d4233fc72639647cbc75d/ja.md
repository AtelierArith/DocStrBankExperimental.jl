```
MKLPardisoLU(;iparm::Vector, mtype::Int)

MKLPardisoLU(matrix; iparm, mtype)
```

pardisoに基づくLU因子分解。これを使用するには、`using Pardiso`を発行する必要があります。このバージョンは、IntelのMKLライブラリの2000年代初頭のフォークを使用しています。

オプションのキーワード引数`mtype`と`iparm`は、[Pardiso内部パラメータ](https://github.com/JuliaSparse/Pardiso.jl#readme)です。

それらを設定するには、次のように`PardisoSolver`にアクセスすることもできます。

```
using Pardiso
plu=MKLPardisoLU()
Pardiso.set_iparm!(plu.ps,5,13.0)
```
