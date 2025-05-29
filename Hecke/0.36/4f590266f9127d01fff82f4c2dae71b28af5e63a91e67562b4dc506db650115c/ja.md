```
has_complement(f::FinGenAbGroupHom) -> Bool, FinGenAbGroupHom
has_complement(U::FinGenAbGroup, G::FinGenAbGroup) -> Bool, FinGenAbGroupHom
```

群 $G$ の部分群を表す写像、または群 `G` の部分群 `U` を与えると、真と `G` における補群の注入を返すか、偽を返します。

関連情報: [`is_pure`](@ref)
