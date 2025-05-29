```
interleaveby(predicate=Base.isless, a, b)
```

`a` と `b` の交互に選択された要素を反復処理します（デフォルトは小なり）。

入力:

  * `predicate(ak,bk) -> Bool`: 次の要素を `a` から選ぶか (true)、`b` から選ぶか (false) を決定します。
  * `fa(ak)`, `fb(bk)`: 選ばれた要素に適用する関数

```jldoctest
julia> collect(interleaveby(1:2:5, 2:2:6))
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```

もし predicate が `Base.isless`（デフォルト）で、両方の入力がソートされている場合、これはソートされた出力を生成します。もし predicate が状態を持つファンクタで、true-false-true-false... と交互に変わる場合、これはマイクロカレンの定義に記載されているような古典的な交互操作を生成します。
