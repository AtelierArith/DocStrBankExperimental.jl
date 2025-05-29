```
deep_properties(::Type{<:MLJType})
```

`MLJType` サブタイプ `M` の場合、このトレイトの値は "深い" と見なされる `M` の任意のプロパティのタプルであるべきです。

タイプ `M` の二つのインスタンスが `==` または `is_same_except` の意味で等しいかどうかをテストする場合、"深い" プロパティの値（その値が複合型であると仮定される）の値が一致するのは、対応するプロパティ *のそれらのプロパティ値* が `==` である場合と見なされます。

`M` のプロパティのうち、その値自体が `MLJType` であるものは自動的に "深い" と見なされ、トレイトの戻り値には含めるべきではありません。

詳細は [`is_same_except`](@ref) を参照してください。

### 例

`Bar` 型の単一フィールドを持つ `MLJType` サブタイプ `Foo` を考えます。この `Bar` は *MLJType* のサブタイプではありません：

```julia
mutable struct Bar
    x::Int
end

mutable struct Foo <: MLJType
    bar::Bar
end
```

この場合、`Foo` の可変性は `Foo(1) != Foo(1)` を意味し、したがって `MLJType` オブジェクトの定義された `==` によれば（詳細は [`is_same_except`](@ref) を参照）、次のようになります。

```julia
Bar(Foo(1)) != Bar(Foo(1))
```

しかし、次の宣言の後では

```julia
MLJModelInterface.deep_properties(::Type{<:Foo}) = (:bar,)
```

次のようになります。

```julia
Bar(Foo(1)) == Bar(Foo(1))
```
