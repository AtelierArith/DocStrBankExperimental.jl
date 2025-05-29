### parse(T::Type{Dict}, s::AbstractString) -> ::Dict

辞書を解析します。以下の入力例のいずれかを含むことができます：

  * JSONデータ; 例: "{A:5, x:6}"
  * 辞書データ; 例: "A => [5, 10, 15, 20], B => [5, 10, 15, 20]"

**引数**

  * T <: DataType; **s** を解析する型。
  * s <: AbstractString; 型 **T** に解析される文字列。

---

### 例

```
example_input::String = "{x => [5, 10, 15], y = [5, 8, 7]}"
my_dct::Dict = parse(Dict, example_input)

example_input::String = "{x : [5, 10, 15], y : [5, 8, 7]}"
my_dct::Dict = parse(Dict, example_input)

typeof(myint) == Dict
true
```
