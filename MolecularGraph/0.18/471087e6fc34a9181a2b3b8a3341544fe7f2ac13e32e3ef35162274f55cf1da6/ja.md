```
kekulize(mol::SimpleMolGraph) -> Vector{Int}
```

ケクレ化が適用された結合次数の配列を返します。

二重結合と単結合は、SMILESの小文字の原子からなる芳香族環に割り当てられます（これをケクレ化と呼びます）。ケクレ化は、SMILESから解析された分子の価数と暗黙の水素が正しく評価されるために必要です。
