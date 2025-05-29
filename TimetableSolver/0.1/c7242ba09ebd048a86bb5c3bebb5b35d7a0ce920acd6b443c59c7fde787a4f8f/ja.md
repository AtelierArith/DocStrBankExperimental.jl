```
授業
```

時間割の区分を表すための型。

# コンストラクタ

  * `Division(grade::Int, section::Int)`
  * `Division(grade::Int, section::Int, section_str::String)`

# フィールド

  * `grade::Int`: 区分の学年。
  * `section::Int`: 区分のセクション。
  * `section_str::String`: 文字列としての区分のセクション。
  * `__str__::String`: 区分の事前計算された文字列表現。
