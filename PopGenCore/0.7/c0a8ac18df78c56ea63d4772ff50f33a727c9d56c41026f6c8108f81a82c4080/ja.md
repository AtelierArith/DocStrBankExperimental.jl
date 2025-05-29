```
keep!(data::PopData, kwargs...)
```

`PopData`オブジェクトをインプレースで編集し、指定されたキーワードの出現のみを保持します。複数のフィールドを使用する場合、それらは「`or`」文として連結されます。すべての値はフィルタリングのために`String`に変換されるため、`Symbol`や数字も機能します。これは、PopDataのサブセットまたはフィルタリングのためのよりシンプルで基本的な構文と見なすことができます。

### キーワード引数

#### `locus`

`PopData`内で保持したいローカスの`String`または`Vector{String}`。

#### `population`

`PopData`内で保持したい集団の`String`または`Vector{String}`。

#### `name`

`PopData`内で保持したいサンプルの`String`または`Vector{String}`。

**例**

```
cats = @nancycats;
keep!(cats, population = 1:5)

# 4つの集団と3つの特定のサンプルを保持
keep!(cats, name = ["N100", "N102", "N211"])

# 2つのローカス、2つの集団、10人の特定の個体を保持
keep!(cats, locus = [:fca8, "fca37"], population = [7,8], name = samplenames(cats)[1:10])
```
