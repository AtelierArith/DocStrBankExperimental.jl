```
Table([options], ...; ...)
```

オプションを持つ表形式データで、PGFPlotsの`table[options] { ... }`に対応します。

`options`はオプションを格納します。これに続いて`AbstractString`がある場合、それはデータを読み込むためのファイル名として使用されます。そうでない場合、すべての引数は[`TableData`](@ref)に渡されます。

例:

```julia
Table(["x" => 1:10, "y" => 11:20])        # ベクターから

Table([1:10, 11:20])                      # 同じ内容、名前なし

Table(Dict(:x => 1:10, :y = 11:20))       # シンボルを持つDict

@pgf Table({ "x index" = 2, "y index" = 1 }, randn(10, 3))

let x = range(0; stop = 1, length = 10), y = range(-2; stop =  3, length = 15)
    Table(x, y, sin.(x + y'))             # エッジと行列
end
```
