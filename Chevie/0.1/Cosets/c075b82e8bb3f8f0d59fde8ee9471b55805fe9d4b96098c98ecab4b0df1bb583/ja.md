`subspets(WF,I,w=one(Group(WF)))`

`WF` のコセットの反射サブコセットを返します。グループ `reflection_subgroup(Group(WF),I)` とトーション `w*WF.phi` を持ちます。`w` は `Group(WF)` の要素であり、`w*WF.phi` が `I` によって生成されるサブルートシステムを正規化する必要があります。

```julia-repl
julia> WF=spets(coxgroup(:F,4))
F₄

julia> w=transporting_elt(Group(WF),[1,2,9,16],[1,9,16,2],ontuples);

julia> LF=subspets(WF,[1,2,9,16],w)
F₄₍₁‚₂‚₉‚₁₆₎=³D₄₍₃₄₁₂₎

julia> diagram(LF)
ϕ acts as (2,3,4) on the component below
  O 4
  ￨
O—O—O D₄
3 1 2
```
