```
get_solutions(
    res::Result, x::String;
    branches=1:branch_count(res), realify=false, class=["stable"], not_class=[]
    )
get_solutions(res::Result; branches=1:branch_count(res), class=["stable"], not_class=[])
```

`Result`オブジェクトから、`class`キーワードで指定されたフィルタリング基準に基づいて解ベクトルを抽出します。最初のメソッドは、名前`x`で特定の解成分を抽出することを可能にします。2番目のメソッドは、完全な解ベクトルを返します。

# キーワード引数

  * `branches=1:branch_count(res)`: 出力に含めるブランチの範囲
  * `realify=false`: 複素解を実数形式に変換するかどうか
  * `class=["physical", "stable"]`: 含める分類ラベルの配列
  * `not_class=[]`: 除外する分類ラベルの配列

# 戻り値

指定された基準に一致するフィルタリングされた解ベクトル
