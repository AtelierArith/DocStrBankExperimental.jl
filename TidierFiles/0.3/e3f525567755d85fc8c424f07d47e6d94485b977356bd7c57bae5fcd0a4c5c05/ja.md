```
read_json(path::String; null = missing, convertMixedNumberTypes::Bool = true)
```

JSONファイルからデータをDataFrameに読み込む

# 引数

  * `path::String`: JSONファイルのファイル名またはURL
  * `null`: JSONのnullがどのデータ型であるべきかを決定します
  * `convertMixedNumberTypes::Bool`: JSON内の数値を解析する際、Float64またはInt64として解釈される可能性があります。このフラグをtrueに設定すると、混合数値（同じ列内）がFloat64として解釈されます

# 例

```julia

julia> df = read_json("https://raw.githubusercontent.com/vega/vega-datasets/refs/heads/main/data/movies.json")
3201×16 DataFrame
  Row │ Director         Worldwide Gross  Running Time min  US DVD Sales  Source                        Distributor  ⋯
      │ String?          Int64?           Int64?            Int64?        String?                       String?      ⋯
──────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────
    1 │ missing                   146083           missing       missing  missing                       Gramercy     ⋯
    2 │ missing                    10876           missing       missing  missing                       Strand
  ⋮   │        ⋮                ⋮                ⋮               ⋮                     ⋮                        ⋮    ⋱
 3200 │ Martin Campbell        141475336               129       missing  Remake                        Sony Picture
 3201 │ Martin Campbell        233700000               136       missing  Remake                        Sony Picture
```
