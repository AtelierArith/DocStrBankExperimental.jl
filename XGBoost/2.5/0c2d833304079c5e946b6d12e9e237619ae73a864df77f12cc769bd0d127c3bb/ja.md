```
importancetable(b::Booster)
```

`b`のすべての利用可能な特徴重要度統計の要約を提供する、Table.jl互換のテーブル（`Vector`の名前付きタプル）を返します。このテーブルは主に表示目的で使用されます。重要度統計を取得するより直接的な方法については[`importance`](@ref)を参照してください。このテーブルの便利な表示については[`importancereport`](@ref)を参照してください。
