```
nmap = emaptonmap(emap, mol, query)
```

[`edge_substruct_matches`](@ref) によって返される形式のエッジベースのマッピングを、ノード間のマップに変換します。一般的に、`nmap[i]` は長さ1のベクトル `[j]` であり、`i=>j` は `nodeattr(query, i)` から `nodeattr(mol, j)` へのマッピングです。マッピングが曖昧な場合、`nmap[i]` は多値になることがあります。
