```
locale_id([gloc::Locale, ]category)
```

指定されたカテゴリに対して、ロケール変数に保存されている現在のロケールIDを決定します。glocが指定されていない場合は、タスク固有のロケール変数を使用します。有効なカテゴリ名がない場合は例外をスローします。有効なカテゴリは次のとおりです: :CTYPE, :COLLATE, :MESSAGES, :MONETARY, :NUMERIC, :TIME
