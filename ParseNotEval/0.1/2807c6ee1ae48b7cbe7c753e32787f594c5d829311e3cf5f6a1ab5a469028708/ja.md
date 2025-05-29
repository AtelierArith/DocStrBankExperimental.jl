### parse(T::Type{String}, s::AbstractString) -> ::String

文字列を文字列に解析することは必要ではありませんが、バインディングが存在する理由は、次元が型によって解析される場合でも、文字列であれば通常の戻り値を持つことができるからです。 **引数**

  * T <: DataType; **s** を解析する型。
  * s <: AbstractString; 型 **T** に解析される文字列。

---

### 例

```
example_input = "5"
myint::Int64 = parse(String, example_input)
typeof(myint) == String
true
```
