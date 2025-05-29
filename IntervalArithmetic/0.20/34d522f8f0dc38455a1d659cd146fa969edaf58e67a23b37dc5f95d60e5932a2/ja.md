```
@format [style::Symbol] [decorations::Bool] [sigfigs::Integer]
```

`@format` マクロは、区間の出力形式を制御するためのシンプルなインターフェースを提供します。これらのオプションは `setformat` 関数に渡されます。新しい `DisplayParameters` オブジェクトを返します。

引数は任意の順序で、次の型である必要があります：

  * `Symbol`: 出力形式（`:full`、`:standard` または `:midpoint`）
  * `Bool`: 装飾を表示するかどうか
  * `Integer`: 有効数字の数

例：

```
julia> x = 0.1..0.3
@[0.0999999, 0.300001]

julia> @format full
Display parameters:
- format: full
- decorations: false
- significant figures: 6

julia> x
Interval(0.09999999999999999, 0.30000000000000004)

julia> @format standard 3
Display parameters:
- format: standard
- decorations: false
- significant figures: 3

julia> x
[0.0999, 0.301]
```
