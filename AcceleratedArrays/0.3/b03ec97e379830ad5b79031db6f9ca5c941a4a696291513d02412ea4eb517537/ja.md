```
Interval(start, stop)
```

閉区間を構築します。これは、`isless` に従って `start` と `stop` の間（両端を含む）の要素を含むコレクションです（`in` を介して）。このコレクションは抽象的な性質を持ち、反復、インデックス付けなどはサポートしていません。

`..` 関数を介して構築できます。例えば、`1..3 === Interval(1, 3)` です。

# 例

```julia julia> 2 in Interval(1, 3) true

julia> 3 in Interval(1, 3) true

julia> 4 in Interval(1, 3) false
```
