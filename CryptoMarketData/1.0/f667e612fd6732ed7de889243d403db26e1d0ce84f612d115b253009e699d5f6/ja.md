```julia
save!(exchange, market; datadir, startday, endday, delay)

```

指定された取引所と市場から1分間隔のキャンドルをダウンロードし、ローカルに保存します。

# キーワード引数

  * datadir="./data" - 保存されたデータが格納されるディレクトリ
  * startday - キャンドルの取得を開始する`Date`
  * endday - キャンドルの取得を停止する`Date`
  * delay - `sleep()`に渡される遅延で、`save_day!()`への内部呼び出しの間に一時停止します

# 例

```julia-repl
julia> bitstamp = Bitstamp()
julia> save!(bitstamp, "BTC/USD", endday=Date("2020-08-16"))
```
