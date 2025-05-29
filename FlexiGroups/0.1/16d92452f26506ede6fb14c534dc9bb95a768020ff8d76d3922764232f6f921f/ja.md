```
addmargins(grouping; [combine=flatten])
```

`group`または`groupmap`の結果に、グループキーコンポーネントのすべての組み合わせに対してマージンを追加します。

たとえば、データセットが`a`と`b`でグループ化されている場合（`keyf=x -> (;x.a, x.b)`が`group`で）、これは各`a`の値と各`b`の値ごとにグループを追加します。

`combine`は、複数のグループがマージンにどのように結合されるかを指定します。デフォルトの`combine=flatten`は、すべての関連グループを単一のコレクションに連結します。

# 例

```julia
xs = [(a=1, b=:x), (a=2, b=:x), (a=2, b=:y), (a=3, b=:x), (a=3, b=:x), (a=3, b=:x)]
# aとbのユニークな組み合わせによる基本的なグループ化
g = group(xs)
map(length, g) == dictionary([(a=1, b=:x) => 1, (a=2, b=:x) => 1, (a=2, b=:y) => 1, (a=3, b=:x) => 3])

# マージンを追加
gm = addmargins(g)
map(length, gm) == dictionary([
    (a=1, b=:x) => 1, (a=2, b=:x) => 1, (a=2, b=:y) => 1, (a=3, b=:x) => 3,  # 元のグループ化結果
    (a=1, b=total) => 1, (a=2, b=total) => 2, (a=3, b=total) => 3,  # aのすべての値のマージン
    (a=total, b=:x) => 5, (a=total, b=:y) => 1,  # bのすべての値のマージン
    (a=total, b=total) => 6,  # 合計
])
```
