```
strValue(f::Value)
```

`Value`[@ref]オブジェクトの`:compact => true`表現の文字列式

#### 例:

```
julia> f = Value(1,"Hz")
Value(1, "Hz")

julia> strValue(f)
"1 Hz"
```
