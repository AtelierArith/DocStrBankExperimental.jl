### parse(T::Type{Array}, s::AbstractString) -> ::Array{typeof(parse(Any, **s**))}

**s**を型**T**に解析します。**引数**

  * T <: DataType; **s**を解析する型。
  * s <: AbstractString; 型**T**に解析される文字列。

---

### 例

```
example_input = "[5, 10, 15, 20]"
my_array::Array{Int64} = parse(Array, example_input)
[5, 10, 15, 20]
my_array::Array{Float64} = parse(Float64, my_array)
[5.0, 10.0, 15.0, 20.0]
```
