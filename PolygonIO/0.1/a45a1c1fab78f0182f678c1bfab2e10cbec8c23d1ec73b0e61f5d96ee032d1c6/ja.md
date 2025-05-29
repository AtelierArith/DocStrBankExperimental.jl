```
PolyOpts <: AbstractPolyOptions
```

PolygonIOのユーザーオプション。

# オプション

  * api_key: 登録されたpolygon.ioアカウントからのAPIキーを表す文字列。
  * table: 抽出された結果をテーブルとして変換するかどうか。Table.jlと互換性があるか、生のJSONの場合はnothing。

# 例

```julia-repl
julia> using PolygonIO, DataFrames
julia> opts = PolyOpts(API_KEY, DataFrame)  # ユーザーが表形式の出力を希望する場合
julia> opts = PolyOpts(API_KEY, nothing)    # ユーザーが生のJSON出力を希望する場合
```
