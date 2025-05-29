```
initialize_auxiliary(model::AbstractModel, state::NamedTuple)
```

`model`のための必要な構造を持つ補助変数のNamedTupleを返し、その値は`similar(state)`に等しいです。これは、すべての補助変数が全体のドメインにわたって定義されており、すべての補助変数が同じ次元と型を持つことを前提としています。補助変数のNamedTupleは、フィールドではない事前割り当てされたオブジェクトも保持できます。

モデルに補助変数がない場合、返されるNamedTupleには空の配列のみが含まれます。

入力`state`は、通常はClimaCoreフィールドまたはVector{FT}のような配列のようなオブジェクトです。

これに対する調整 - たとえば、異なる補助変数が異なる次元を持つため - は、新しいメソッドを定義する必要があります。
