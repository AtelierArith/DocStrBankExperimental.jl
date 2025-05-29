### parse(T::Type{Symbol}, s::AbstractString) -> ::Symbol

シンボルを解析します。コロンなしで。これは、コンストラクタ Symbol(::AbstractString) への単純なバインドされた呼び出しです。 **引数**

  * T <: DataType; 解析する型 **s**。
  * s <: AbstractString; 型 **T** に解析される文字列。

---

### 例

```
example_input::String = "hello"
symb::Symbol = parse(Symbol, example_input)

:hello

typeof(myint) == Symbol
true
```
