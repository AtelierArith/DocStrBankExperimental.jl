```
Learn(train, model, features => targets)
```

統計学習 `model` を `train` テーブルにフィットさせ、`features` と `targets` のセレクタを使用します。

# 例

```julia
Learn(train, model, [1, 2, 3] => "d")
Learn(train, model, [:a, :b, :c] => :d)
Learn(train, model, ["a", "b", "c"] => 4)
Learn(train, model, [1, 2, 3] => [:d, :e])
Learn(train, model, r"[abc]" => ["d", "e"])
```
