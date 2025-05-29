```
t = Table(nrows, ncols)
t = Table(nrows, ncols, colwidth, rowheight)
t = Table(rowheights, columnwidths)
```

テーブルは `O` で中央に配置されますが、仕様の後にポイントを指定することもできます。

```
t = Table(nrows, ncols, centerpoint)
t = Table(nrows, ncols, colwidth, rowheight, centerpoint)
t = Table(rowheights, columnwidths, centerpoint)
```

## 例

シンプルなテーブル

```
t = Table(4, 3) # 4 行 3 列、デフォルトは 100w, 50 h
t = Table(4, 3, 80, 30)   # 4 行 30pts 高、3 列 80pts 幅
t = Table(4, 3, (80, 30)) # 同じ
t = Table((4, 3), (80, 30)) # 同じ
```

数量の代わりに行の高さと列の幅を指定します：

```
t = Table([60, 40, 100], 50) # 3 つの異なる高さの行、1 列 50 幅
t = Table([60, 40, 100], [100, 60, 40]) # 3 行、3 列
t = Table(fill(30, (10)), [50, 50, 50]) # 10 行 30 高、3 列 10 幅
t = Table(50, [60, 60, 60]) # 1 行 (50 高)、3 列 60 幅
t = Table([50], [50]) # 1 行、1 列、両方 50 単位幅
t = Table(50, 50, 10, 5) # 50 行、50 列、10 単位幅、5 単位高
t = Table([6, 11, 16, 21, 26, 31, 36, 41, 46], [6, 11, 16, 21, 26, 31, 36, 41, 46])
t = Table(15:5:55, vcat(5:2:15, 15:-2:5))
 #  テーブルには 108 セルがあり、次のようになります：
 #  行の高さ: 15 20 25 30 35 40 45 50 55
 #  列の幅:  5 7 9 11 13 15 15 13 11 9 7 5
t = Table(vcat(5:10:60, 60:-10:5), vcat(5:10:60, 60:-10:5))
t = Table(vcat(5:10:60, 60:-10:5), 50) # 1 列 50 単位幅
t = Table(vcat(5:10:60, 60:-10:5), 1:5:50)
```

テーブルはイテレータであり、各イテレーションで次のタプルを返します：

  * 行と列に配置されたセルの中心の `x`/`y` ポイント（現在の 0/0 に対して）
  * セルの番号（左から右、次に上から下）

`nrows`/`ncols` は必要な行数と列数です。

イテレーション中に現在の行と列を知ることが役立つことがあります：

```julia
t.currentrow
t.currentcol
```

行の高さと列の幅は次のように取得できます：

```julia
t.rowheights
t.colwidths
```

`box(t::Table, r, c)` を使用してテーブルセルを塗りつぶすことができます：

```julia
@svg begin
    for (pt, n) in (t = Table(8, 3, 30, 15))
        randomhue()
        box(t, t.currentrow, t.currentcol, :fill)
        sethue("white")
        text(string(n), pt)
    end
end
```

または、イテレーションなしでセル番号を使用して：

```julia
@svg begin
    t = Table(8, 3, 30, 15)
    for n in eachindex(t)
        randomhue()
        box(t, n, :fill)
        sethue("white")
        text(string(n), t[n])
    end
end
```

テーブルを使用してグリッドポイントを作成するには：

```julia-repl
julia> first.(collect(Table(10, 6)))
60-element Vector{Point}:
 Luxor.Point(-10.0, -18.0)
 Luxor.Point(-6.0, -18.0)
 Luxor.Point(-2.0, -18.0)
 ⋮
 Luxor.Point(2.0, 18.0)
 Luxor.Point(6.0, 18.0)
 Luxor.Point(10.0, 18.0)
```

これは、テーブル内のセルの中心点であるポイントの配列を返します。

## セルの選択

`getcells(table, rows, columns)` を使用してセルを選択できます。これにより、`(point, index)` タプルのリストが返されます。

  * `getcells(t, :, :)` はすべてのセルのリストを返します
  * `getcells(t, 1, :)` は行 1 のすべてのセルのリストを返します
  * `getcells(t, :, 3)` は列 3 のすべてのセルのリストを返します
  * `getcells(t, 2:4, [3, 5])` は行 2-4、列 3 と 5 のセルのリストを返します

```
