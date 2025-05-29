```
getcells(t, rows, columns)
```

`t`に対応する行と列のTilerまたはTableのセルを取得します。

  * `t`はTilerまたはTableです
  * `rows`は行番号の配列または範囲です
  * `cols`は列番号の配列または範囲です

`:`を使用して「すべての行」または「すべての列」を指定します。

各Tupleが`(Point, Number)`であるTupleの配列を返します。

`markcells()`は、この関数の結果を使用して選択したセルにマークを付けることができます。

## 例

```julia
@draw begin
    chessboard = Tiler(600, 600, 8, 8)
    # 奇数行 奇数列
    s = getcells(chessboard, 1:2:12, 1:2:12)
    markcells(chessboard, s, action = :fill)
    # 偶数行 偶数列
    s = getcells(chessboard, 2:2:12, 2:2:12)
    markcells(chessboard, s, action = :fill)
end
```
