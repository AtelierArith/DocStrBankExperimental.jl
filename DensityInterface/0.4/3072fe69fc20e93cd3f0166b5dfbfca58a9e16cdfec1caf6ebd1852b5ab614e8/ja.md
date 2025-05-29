```
densityof(object)
```

オブジェクト `object` の密度（またはその関連する密度）を与えられた点で計算する関数を返します。

```jldoctest a
julia> f = densityof(object);

julia> f(x) == densityof(object, x)
true
```

`densityof(object)` はデフォルトで `Base.Fix1(densityof, object)` に設定されていますが、特化することも可能です。
