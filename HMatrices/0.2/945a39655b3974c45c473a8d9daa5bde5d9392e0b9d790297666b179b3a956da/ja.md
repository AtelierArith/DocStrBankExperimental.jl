```
struct StrongAdmissibilityStd
```

この条件の下で、2つのブロックは、最小の `diameter` がそれらの間の `distance` の `eta` 倍より小さい場合に許容されます。ここで、`eta::Float64` はパラメータです。

## 使用法:

```julia
adm = StrongAdmissibilityStd(;eta=2.0)
adm(Xnode,Ynode)
```
