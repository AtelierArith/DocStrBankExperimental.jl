```
@using LongModuleName as alias
```

モジュール `LongModuleName` を `using` でロードし、`alias` にバインドします。おおよそ次のように等価です。

```julia
using LongModuleName
const alias = LongModuleName
```
