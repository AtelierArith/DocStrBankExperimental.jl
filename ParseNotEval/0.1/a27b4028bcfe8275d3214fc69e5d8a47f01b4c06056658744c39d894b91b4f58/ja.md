### parse(T::Type{Pair}, s::AbstractArray) -> ::Array{T}

**s** の各要素を型 **T** にパースします。キャストできない引数は missing で置き換えます。**引数**

  * T <: DataType; **s** をパースする型。
  * s <: AbstractArray; キャストされる配列。

---

### 例

```
example_input = ["55", "82", "hello"]
new = parse(Int64, example_input)
new
[55, 82, missing]
```
