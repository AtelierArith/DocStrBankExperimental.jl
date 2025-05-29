```
fetch_tles(fetcher::CelestrakTleFetcher; kwargs...) -> Union{Nothing, Vector{TLE}}
```

CelestrakからTLEを取得するには、`fetch`を使用し、`kwargs...`のパラメータを指定します。

この関数は、取得したTLEを含む`Vector{TLE}`を返します。エラーが見つかった場合は、`nothing`を返します。

# キーワード

  * `international_designator::Union{Nothing, AbstractString}`: Celestrak形式の国際設計者 `YYYY-NNN`、ここで`YYYY`は打ち上げ年、`NNN`は打ち上げ番号です。 (**デフォルト**: `nothing`)
  * `satellite_number::Union{Nothing, Number}`: 衛星カタログ番号（NORAD）。 (**デフォルト** = `nothing`)
  * `satellite_name::Union{Nothing, AbstractString}`: 衛星名。この文字列を含むすべての衛星をシステムが検索します。 (**デフォルト**: `nothing`)

!!! note
    検索パラメータは1つのみサポートされています。複数指定された場合、優先順位は次のとおりです: 1) `satellite_number`; 2) `international_designator`; 3) `satellite_name`。


!!! note
    検索パラメータが提供されない場合、関数はエラーをスローします。

