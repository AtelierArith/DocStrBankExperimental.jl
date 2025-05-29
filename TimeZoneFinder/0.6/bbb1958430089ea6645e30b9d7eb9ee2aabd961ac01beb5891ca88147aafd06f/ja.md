```
timezones_at(latitude, longitude)
```

指定された `latitude` と `longitude` で使用されるタイムゾーンを取得します。

タイムゾーンが知られていない場合、空のリストが返されます。逆に、座標が争われている地域にある場合、すべての適用可能なタイムゾーンが返されます。

```jldoctest
julia> timezones_at(52.5061, 13.358)
1-element Vector{Dates.TimeZone}:
 Europe/Berlin (UTC+1/UTC+2)

julia> timezones_at(69.8, -141)
2-element Vector{Dates.TimeZone}:
 America/Anchorage (UTC-9/UTC-8)
 America/Dawson (UTC-7)
```

!!! note
    ライブラリは、`TimeZones` で現在使用されている tzdata のバージョンと互換性のあるタイムゾーン境界ビルダー データのバージョンを使用します。

    名目上、これは `TimeZones` で使用されているのと *同じ* バージョンになりますが、場合によっては古いバージョンが使用されることがあります。

    これには2つの可能な理由があります：

    ```
    1. tzdata リリースに境界の変更がなかったため、この特定のバージョンの境界リリースは
        決して存在しないことを意味します。
    2. 新しい tzdata リリースの境界データセットがまだ利用できない。
    ```

