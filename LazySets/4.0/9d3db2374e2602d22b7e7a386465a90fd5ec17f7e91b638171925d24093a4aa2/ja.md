```
addconstraint!(P::AbstractHPolygon, constraint::HalfSpace;
               [linear_search]::Bool=length(P.constraints) < 10,
               [prune]::Bool=true)
```

ポリゴンに線形制約を追加し、制約をその法線方向によってソートされた状態に保ちます。

### 入力

  * `P`             – 制約表現のポリゴン
  * `constraint`    – 追加する線形制約
  * `linear_search` – （オプション、デフォルト: `length(constraints) < 10`）線形検索と二分検索のどちらを選択するかのフラグ
  * `prune`         – （オプション、デフォルト: `true`）最終的に冗長な制約を削除するためのフラグ
