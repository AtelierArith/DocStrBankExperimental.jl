### parse(T::Type{Date}, s::AbstractString) -> ::Date

文字列から日付に適切な形式で日付を解析します。'-'区切りが必要です。 **引数**

  * T <: DataType; 解析する型 **s** の型。
  * s <: AbstractString; 型 **T** に解析される文字列。

---

### 例

```
example_input::String = "1999-11-23"
symb::Date = parse(Date, example_input)
typeof(myint) == Date
true
```
