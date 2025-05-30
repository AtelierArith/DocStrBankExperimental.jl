```
Tangent{P, T} <: StructuralTangent{P} <: AbstractTangent
```

この型は、`struct`/`NamedTuple`、または`Tuple`の接線を表します。`P`は、これが接線である対応する原始型です。

`Tangent{P}`は、原始型のフィールドのサブセットに一致するフィールド（技術的にはプロパティ）を持つべきであり、それぞれはそのフィールドの原始型に一致する接線型である必要があります。Pのフィールドで、Tangentに存在しないものは`Zero`として扱われます。

`T`は、バックデータ構造を表す実装の詳細です。Tupleの場合はTupleになり、それ以外のすべての場合は`NamedTuple`になります。ユーザーによって渡されるべきではありません。

`Tuple`の`Tangent`では、`iterate`と`getindex`がタプルと同様に動作するようにオーバーロードされています。`struct`の`Tangent`では、`getproperty`がオーバーロードされ、`tangent.fieldname`を介して値にアクセスできるようになります。`Tangent`に明示的に存在しないフィールドは、`ZeroTangent()`に設定されていると見なされます。`Tangent`が原始のすべてのフィールドを持つようにするために、[`canonicalize`](@ref)関数が提供されています。
