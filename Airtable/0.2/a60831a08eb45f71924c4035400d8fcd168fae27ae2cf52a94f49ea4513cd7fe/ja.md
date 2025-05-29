```
AirRecord(id::String, table::AirTable, fields::NamedTuple)
```

[Airtable レコード](https://support.airtable.com/hc/en-us/articles/360021333094-Getting-started-tables-records-and-fields)のラッパーで、ユニークな識別子、親 [`AirTable`](@ref)、および NamedTuple に格納されたフィールドの値を含みます。

通常、これらを自分で作成することはありませんが、API クエリから返されます。

フィールドの値には [`getindex`](@ref `Base.getindex(::AirRecord, ::Symbol)`) を使用してアクセスできます。
