```julia
Coordinates(itr)

```

引数を、任意の反復可能なオブジェクトから座標に変換します。

具体的には、

  * `Coordinate` と `Nothing` は *そのまま* 渡されます、
  * 有限の実数または文字列の2要素または3要素のタプルは座標として解釈されます、
  * `()` および非有限数を含むタプルは `nothing` になります（空の行を表します）。

結果として得られる座標は、次元の整合性がチェックされます。

## 例

以下は同等です：

```julia
Coordinates((x, 1/x) for x in -5:5)
Coordinates(x == 0 ? () : (x, 1/x) for x in -5:5)
Coordinates(x == 0 ? nothing : Coordinate((x, 1/x)) for x in -5:5)
```

`enumerate` を使用して、既存の `y` 座標に `x` 軸の 1, 2, … を追加します：

```julia
Coordinates(enumerate([1, 4, 9]))
```
