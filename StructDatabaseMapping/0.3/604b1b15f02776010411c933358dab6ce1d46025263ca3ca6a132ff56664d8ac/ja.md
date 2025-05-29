```
mutable struct Nullable{T} <: AbstractNullable{T}
```

外部キーモデルフィールド

外部キーフィールドは、T要素または何もない状態で構築できます。`loaded`フィールドは、外部要素の遅延読み込みに使用されます。外部要素が読み込まれると、`loaded`属性はtrueに設定されます。

```
struct ModelA <: Model ... end
struct ModelB <: Model
    ...
    foreign_field::ForeignKey{ModelA}
end
```
