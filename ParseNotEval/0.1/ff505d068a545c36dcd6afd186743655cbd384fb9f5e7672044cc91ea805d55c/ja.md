### parse(T::Type{Any}, s::AbstractString) -> ::Any

文字列の型を暗黙的に推測しようとします。型をより明示的に仮定するには、最初の引数として型を渡してみてください。 **引数**

  * T <: DataType; **s** を解析する型。
  * s <: AbstractString; 型 **T** に解析される文字列。

---

### 例

```
example_input = "[5, 10, 15, 20]"
my_array::Array{Int64} = parse(Array, example_input)
[5, 10, 15, 20]

example_input = "5"
myint::Int64 = parse(Any, example_input)
```
