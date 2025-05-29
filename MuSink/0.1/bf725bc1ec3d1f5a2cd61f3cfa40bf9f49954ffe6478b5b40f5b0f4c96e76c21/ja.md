```
transport(plan::Coupling, i, j; conditional = false)
transport(plan::Coupling, (i, j); conditional = false)

transport(plan::Coupling, is, js; conditional = false)
transport(plan::Coupling, (is, js); conditional = false)

transport(ws::Workspace, a, b, i, j; conditional = false)
transport(ws::Workspace, a, b, (i, j); conditional = false)

transport(ws::Workspace, a, b, is, js; conditional = false)
transport(ws::Workspace, a, b, (is, js); conditional = false)
```

ノード `a` のピクセル `(i,j)` での結合 `plan` の評価を返します。イテラブル `is` と `js` が提供されると、輸送配列のベクトルが返されます。

`conditional = true` の場合、輸送配列は合計して1になります。

ワークスペース `ws` と2つのノード `a` と `b` が提供されると、対応する結合が暗黙的に計算されます。
