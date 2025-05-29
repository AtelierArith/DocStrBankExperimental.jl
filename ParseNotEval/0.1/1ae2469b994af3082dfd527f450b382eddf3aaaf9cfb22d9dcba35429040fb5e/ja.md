### parse(T::Type{Pair}, s::Pair) -> ::Pair{Symbol, T}

ペア値 **s[2]** を型 **T** に解析します。 **引数**

  * T <: DataType; **s** を解析する型。
  * s <: AbstractArray; キャストされる配列。

---

### 例

```
example_input::Pair = :A => "5"
new::Pair = parse(Int64, example_input)
new
:A => 5
```
