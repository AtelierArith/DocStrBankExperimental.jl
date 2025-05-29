```
PardisoLU(;iparm::Vector, 
           dparm::Vector, 
           mtype::Int)

PardisoLU(matrix; iparm,dparm,mtype)
```

Pardisoに基づくLU因子分解。これを使用するには、`using Pardiso`を発行し、[pardiso-project.org](https://pardiso-project.org)から[pardisoライブラリ](https://github.com/JuliaSparse/Pardiso.jl#pardiso-60)を[インストール](https://github.com/JuliaSparse/Pardiso.jl#pardiso-60)する必要があります。

オプションのキーワード引数`mtype`、`iparm`、および`dparm`は、[Pardiso内部パラメータ](https://github.com/JuliaSparse/Pardiso.jl#readme)です。

それらを設定するために、`PardisoSolver`にアクセスすることもできます。例えば、次のようにします。

```
using Pardiso
plu=PardisoLU()
Pardiso.set_iparm!(plu.ps,5,13.0)
```
