```
window(var::OutputVar, dim_name; left = nothing, right = nothing)
```

与えられた `dim` 次元の値の中から `left` と `right` の間にある値を選択して新しい OutputVar を返します。

`left` および/または `right` が `nothing` の場合、配列の始まり（または終わり）を仮定します。

時間次元の場合、`left` と `right` は `Dates.DateTime` でも構いません（`var` に `start_date` が含まれている場合）。

# 例

```julia
window(var, 'lat', left = -50, right = 50)
window(var, 'time', left = DateTime(2008), right = DateTime(2009))
```

!!! compat "日付と一般化された次元名のサポート"
    `DateTime` を使用して `window` を呼び出し、ファイル内の実際の名前の代わりにその名前の1つで次元を指定することは、ClimaAnalysis v0.5.17 で導入されました。

