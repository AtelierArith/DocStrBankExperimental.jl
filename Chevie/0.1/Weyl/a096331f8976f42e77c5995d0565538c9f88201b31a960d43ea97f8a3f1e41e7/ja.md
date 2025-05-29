`rootdatum(C::AbstractMatrix)` は、Cartan 行列 `C` からの随伴ルートデータです。これは `rootdatum(one(C),C)` と同じです。随伴群は、`coxeter_group(type,rank)` に対してもデフォルトで返されます。以下のメソッドはすべて `pgl₃` を定義します。

```julia-repl
julia> rootdatum(cartan(:A,3))==coxgroup(:A,3)
true

julia> rootdatum(:pgl,3)
pgl₃
```
