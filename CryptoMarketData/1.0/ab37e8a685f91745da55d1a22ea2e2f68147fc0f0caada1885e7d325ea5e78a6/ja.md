```julia
load(exchange, market; datadir, span, tf, table)

```

指定された取引所と市場のキャンドルをファイルシステムからロードします。

# キーワード引数

  * datadir="./data" - 保存されたデータが格納されているディレクトリ
  * span - キャンドルをロードする日付を定義する `Date` スパン。 `missing` の場合はすべてをロードします。
  * tf - 1分のキャンドルをより高い時間枠に集約するために使用される `Period`。
  * table - キャンドルをロードするための Tables.jl 互換の構造体。デフォルトは `DataFrame` です。

# 例

```julia-repl
julia> bitstamp = Bitstamp()
julia> btcusd4h = load(bitstamp, "BTC/USD"; span=Date("2024-01-01"):Date("2024-02-10"), tf=Hour(4))
```
