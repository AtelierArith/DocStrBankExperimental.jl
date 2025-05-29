```
timezone_at(latitude, longitude)
```

指定された `latitude` と `longitude` に適用可能なユニークなタイムゾーンを取得します。

```jldoctest
julia> timezone_at(52.5061, 13.358)
Europe/Berlin (UTC+1/UTC+2)
```

使用される tzdata のバージョンに関する [`timezone_at`](@ref) のドキュメント文字列に関する追加の注意を参照してください。

# 戻り値

  * `latitude` と `longitude` がユニークなタイムゾーンに対応する場合は `TimeZone` インスタンス。
  * タイムゾーンが見つからない場合は `nothing`。

この場所に複数のタイムゾーンが対応する場合は例外が発生します - すべての一致を取得するには [`timezones_at`](@ref) を使用してください。
