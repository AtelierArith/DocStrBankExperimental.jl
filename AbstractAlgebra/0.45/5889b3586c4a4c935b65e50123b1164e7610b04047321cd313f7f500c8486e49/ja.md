```
@attributes typedef
```

これは、`typedef`という式で宣言された型に属性のストレージが確保されることを保証するヘルパーマクロです。`typedef`は、`mutable struct`の定義式である必要があるか、`mutable struct`型の名前である必要があります。

後者のバリアントは、他のパッケージで定義された型に対して属性ストレージを有効にするために便利です。`@attributes`は冪等性があることに注意してください：属性ストレージがすでに利用可能な型に適用されると、何も行いません。

シングルトン型に対しても属性ストレージがサポートされており、実際には常に有効です。したがって、そのような型にこのマクロを適用する必要はありません。

!!! note
    構造体定義に適用されると、このマクロは構造体に新しいフィールドを追加します。コンストラクタのない構造体の場合、これはデフォルトの内部コンストラクタのシグネチャを変更し、属性ストレージフィールドを含むすべてのフィールドに対して明示的な値を要求します。したがって、通常は以下の例のように明示的なデフォルトコンストラクタを追加する方が好ましいです。


# 例

マクロを構造体定義に適用すると、属性の内部ストレージが結果として得られます：

```jldoctest
julia> @attributes mutable struct MyGroup
           order::Int
           MyGroup(order::Int) = new(order)
       end

julia> G = MyGroup(5)
MyGroup(5, #undef)

julia> set_attribute!(G, :isfinite, :true)

julia> get_attribute(G, :isfinite)
true
```

マクロを型名に適用すると、属性の外部ストレージが結果として得られます：

```jldoctest
julia> mutable struct MyOtherGroup
           order::Int
           MyOtherGroup(order::Int) = new(order)
       end

julia> @attributes MyOtherGroup

julia> G = MyOtherGroup(5)
MyOtherGroup(5)

julia> set_attribute!(G, :isfinite, :true)

julia> get_attribute(G, :isfinite)
true
```
