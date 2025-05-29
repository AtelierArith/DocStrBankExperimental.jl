```
addconstraint!(constraints::Vector{<:HalfSpace}, new_constraint::HalfSpace;
               [linear_search]::Bool=length(P.constraints) < 10,
               [prune]::Bool=true)
```

ソートされた制約のベクターに線形制約を追加し、制約をその法線方向によってソートされたままに保ちます。

### 入力

  * `constraints`    – 線形制約のベクター
  * `new_constraint` – 追加する線形制約
  * `linear_search`  – （オプション、デフォルト:                     `length(constraints) < 10`）線形検索とバイナリ検索のどちらを選択するかのフラグ
  * `prune`          – （オプション、デフォルト: `true`）冗長な制約を最終的に削除するためのフラグ

### アルゴリズム

`prune`がアクティブな場合、新しい制約が冗長かどうかを確認します。制約が冗長でない場合、最初の冗長でない制約が見つかるまで左と右の同じチェックを行います。
