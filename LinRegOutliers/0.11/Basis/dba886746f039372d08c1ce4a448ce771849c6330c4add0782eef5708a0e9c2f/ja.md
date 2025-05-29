```
struct RegressionSetting
    formula::FormulaTerm
    data::DataFrame
end

回帰設定のための不変データ構造。
```

# 引数

  * `formula::FormulaTerm`: 形式オブジェクトは線形回帰モデルを説明します。
  * `data::DataFrame`: DataFrameオブジェクトはデータを保持します。

# 注意事項

```
このパッケージで実装されたメソッドは、RegressionSettingオブジェクトとして線形モデルを受け入れます。
このオブジェクトはモデルの式と回帰推定に使用されるデータを保持します。
```

# 例

```julia-repl
julia> setting = RegressionSetting(@formula(calls ~ year), phones)
RegressionSetting(calls ~ year, 24×2 DataFrame
│ Row │ year  │ calls   │
│     │ Int64 │ Float64 │
├─────┼───────┼─────────┤
│ 1   │ 50    │ 4.4     │
│ 2   │ 51    │ 4.7     │
│ 3   │ 52    │ 4.7     │
│ 4   │ 53    │ 5.9     │
│ 5   │ 54    │ 6.6     │
│ 6   │ 55    │ 7.3     │
│ 7   │ 56    │ 8.1     │
│ 8   │ 57    │ 8.8     │
│ 9   │ 58    │ 10.6    │
│ 10  │ 59    │ 12.0    │
⋮
│ 14  │ 63    │ 21.2    │
│ 15  │ 64    │ 119.0   │
│ 16  │ 65    │ 124.0   │
│ 17  │ 66    │ 142.0   │
│ 18  │ 67    │ 159.0   │
│ 19  │ 68    │ 182.0   │
│ 20  │ 69    │ 212.0   │
│ 21  │ 70    │ 43.0    │
│ 22  │ 71    │ 24.0    │
│ 23  │ 72    │ 27.0    │
│ 24  │ 73    │ 29.0    │)
```
