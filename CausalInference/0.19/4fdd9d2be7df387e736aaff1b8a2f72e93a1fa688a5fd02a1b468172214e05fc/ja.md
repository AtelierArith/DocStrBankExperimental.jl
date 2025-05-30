```
find_min_dsep(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y), veto = no_veto)
```

グラフ `g` における頂点の集合 `X` と `Y` に対して、$I ⊆ Z ⊆ R$ となる包含最小の d-セパレーター `Z` を見つけます。すなわち、どの部分集合も d-セパレーターでない場合に限り、そうでなければ `false` を返します。

http://auai.org/uai2019/proceedings/papers/222.pdf で提案されたアルゴリズム的アプローチに基づいています。
