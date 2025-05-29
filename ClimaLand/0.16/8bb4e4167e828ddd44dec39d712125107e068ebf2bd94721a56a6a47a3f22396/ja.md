```
initialize_prognostic(model::AbstractModel, state::NamedTuple)
```

`model`の必要な構造を持つ予測変数のFieldVectorを返し、その値は`similar(state)`に等しいです。これは、すべての予測変数が全体のドメインにわたって定義されており、すべての予測変数が同じ次元と型を持つことを前提としています。

モデルに予測変数がない場合、返されるFieldVectorは空の配列のみを含みます。

入力`state`は、通常ClimaCore FieldまたはVector{FT}のような配列状のオブジェクトです。

これに対する調整 - たとえば、異なる予測変数が異なる次元を持つため - は、新しいメソッドを定義する必要があります。
