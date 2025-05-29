```
exclude!(data::PopData, kwargs...)
```

`PopData`オブジェクトをインプレースで編集し、指定された情報のすべての出現を除外します。キーワードは任意の組み合わせで使用できます。`omit!`および`remove!`と同義です。すべての値はフィルタリングのために`String`に変換されるため、`Symbol`や数字も機能します。これは、`PopData`のサブセット化またはフィルタリングのためのよりシンプルで基本的な構文と見なすことができます。

### キーワード引数

#### `locus`

`PopData`から削除したいローカスの`String`または`Vector{String}`。キーワード`loci`も機能します。

#### `population`

`PopData`から削除したい集団の`String`または`Vector{String}`。キーワード`populations`も機能します。

#### `name`

`PopData`から削除したいサンプルの`String`または`Vector{String}`。キーワード`names`、`sample`、および`samples`も機能します。

**例** ``` cats = @nancycats; exclude!(cats, name = "N100", population = 1:5) exclude!(cats, name = ["N100", "N102", "N211"], locus = ["fca8", "fca23"]) exclude!(cats, name = "N102", locus = :fca8, population = "3")
