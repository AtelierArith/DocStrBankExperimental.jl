```julia
struct ParsingError <: CTBase.CTException
```

抽象解析中の構文エラーに対してスローされる例外です。

**フィールド**

  * `var::String`
