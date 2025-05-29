```julia
ReCreateSelfCons(checkpoint::Dict, F::T, Update::R) :: SelfCons where {T<:Function, R<:Function}
```

チェックポイント辞書と関数 `F` および `Update`（チェックポイント中に保存されない）から `SelfCons` 構造体を返します。
