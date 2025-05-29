```
findmiss(X)
```

データセット内の欠損データを含む行を見つけます。

  * `X` : データセット。

データフレームについては、`DataFrames.completecases` および `DataFrames.dropmissing` も参照してください。

## 例

```julia
using Jchemo

X = rand(5, 4)
zX = hcat(rand(2, 3), fill(missing, 2))
Z = vcat(X, zX)
findmiss(X)
findmiss(Z)
```
