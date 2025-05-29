```
keep(data::PopData, kwargs...)
```

指定されたキーワードの出現のみを保持する新しい `PopData` オブジェクトを返します。`exclude()` とは異なり、一度に使用できるキーワードは1つだけです。すべての値はフィルタリングのために `String` に変換されるため、`Symbol` や数字も機能します。これは、PopDataのサブセット化またはフィルタリングのためのよりシンプルで基本的な構文と見なすことができます。

### キーワード引数

#### `locus`

保持したいローカスの `String` または `Vector{String}`。

#### `population`

保持したい集団の `String` または `Vector{String}`。

#### `name`

保持したいサンプルの `String` または `Vector{String}`。

**例**

```
cats = @nancycats;
keep(cats, population = 1:5)
# cats[cats.genodata.population .∈ Ref(string.(1:5)), :]

keep(cats, name = ["N100", "N102", "N211"])
# cats[cats.genodata.name .∈ Ref(["N100", "N102", "N211"]), :]

keep(cats, locus = [:fca8, "fca37"])
# cats[cats.genodata.locus .∈ Ref(["fca8", "fca37"]), :]
```
