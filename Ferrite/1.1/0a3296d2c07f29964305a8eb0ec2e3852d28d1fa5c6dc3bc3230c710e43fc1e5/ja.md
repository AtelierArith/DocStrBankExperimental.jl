```
add_constraint_entries!(
    sp::AbstractSparsityPattern, ch::ConstraintHandler;
    keep_constrained::Bool = true,
)
```

制約ハンドラ `ch` からの制約に基づくすべてのエントリをスパースパターンに追加します。この操作はパターン内の既存のエントリに依存するため、スパースパターンを作成する際にはこの関数を*最後の*ステップとして呼び出す必要があります。

# キーワード引数

  * `keep_constrained`: 制約された自由度のエントリをスパースパターンに保持するかどうか（`keep_constrained = true`）または削除するか（`keep_constrained = false`）。
