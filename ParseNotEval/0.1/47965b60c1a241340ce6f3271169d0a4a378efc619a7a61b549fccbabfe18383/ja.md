### parse(T::Type{Pair}, s::AbstractString) -> ::Pair

文字列 **s** を型 **T** に解析します。 **引数**

  * T <: DataType; **s** を解析する型。
  * s <: AbstractString; 型 **T** に解析される文字列。

---

### 例

```
example_input::String = "x => 5"
symb::Pair = parse(Pair, example_input)
typeof(myint) == Pair
true
```
