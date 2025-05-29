### parse(T::Type{DateTime}, s::AbstractString) -> ::DateTime

文字列から日付と時刻を適切なフォーマットで解析します。'-'および':'の区切り文字を使用する必要があります。 **引数**

  * T <: DataType; 解析する型 **s** の型。
  * s <: AbstractString; 型 **T** に解析される文字列。

---

### 例

```
example_input::String = "1999-11-23:8000"
symb::DateTime = parse(DateTime, example_input)
typeof(myint) == DateTime
true
```
