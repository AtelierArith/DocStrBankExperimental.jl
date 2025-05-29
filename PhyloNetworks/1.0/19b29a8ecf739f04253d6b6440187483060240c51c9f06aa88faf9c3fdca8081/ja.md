```
deleteaboveLSA!(net, preorder=true)
```

葉の最も安定した祖先（LSA）より上（祖先にあたる）にあるエッジとノードを削除します。LSAの定義については[`leaststableancestor`](@ref)を参照してください。出力: 修正されたネットワーク`net`。
