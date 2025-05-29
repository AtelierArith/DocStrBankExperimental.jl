The supertype for methods producing or consuming data.

```
                 ╭────loader─────╮
                 ╵               ▼
Storage ◀────▶ Data          Information
                 ▲               ╷
                 ╰────writer─────╯
```

There are three subtypes:

  * `DataStorage`
  * `DataLoader`
  * `DataWrite`

Each subtype takes a `Symbol` type parameter designating the driver which should be used to perform the data operation. In addition, each subtype has the following fields:

  * `dataset::DataSet`, the data set the method operates on
  * `type::Vector{<:QualifiedType}`, the Julia types the method supports
  * `priority::Int`, the priority with which this method should be used, compared to alternatives. Lower values have higher priority.
  * `parameters::SmallDict{String, Any}`, any parameters applied to the method.
