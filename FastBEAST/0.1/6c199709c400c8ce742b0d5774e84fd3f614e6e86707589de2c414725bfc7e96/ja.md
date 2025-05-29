```
create_tree(points::Array{SVector{D, T}, 1}; treeoptions)
```

与えられたデータポイントのセットに対して代数ツリーを作成します。返されるデータ構造は、このパッケージのアルゴリズムの基盤となります。

# 引数

  * `points::Array{SVector{D, T}, 1}`: は、[SVector](https://juliaarrays.github.io/StaticArrays.jl/stable/pages/api/#SVector-1)の配列です。各[SVector](https://juliaarrays.github.io/StaticArrays.jl/stable/pages/api/#SVector-1)は、一般的に2つまたは3つの浮動小数点値を含み、空間内の位置を記述します。

# キーワード

  * `treeoptions::TreeOptions`: このキーワードは、どのツリーが構築されるかを定義します。`TreeOptions`は抽象型であり、`BoxTreeOptions`または[`KMeansTreeOptions`](@ref)のいずれかになります。デフォルトの型は`BoxTreeOptions`です。

# 戻り値

  * `AbstractNode`: 作成されたツリーのルートです。AbstractNodeは抽象型であり、キーワードに応じて`BoxTreeNode`または[`KMeansTreeNode`](@ref)のいずれかになります。
