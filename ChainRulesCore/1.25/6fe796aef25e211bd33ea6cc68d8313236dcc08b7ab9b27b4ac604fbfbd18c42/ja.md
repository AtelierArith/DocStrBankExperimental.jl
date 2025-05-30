```
StructuralTangent{P} <: AbstractTangent
```

`struct` `P`（または `Tuple`/`NamedTuple`）の接線の型を、ミラーリングフィールドを持つオブジェクトとして表現します。

!!! warning "実験的"
    `StructuralTangent` は実験的な機能であり、ミューテーションサポート機能セットの一部です。`StructuralTangent` コンストラクタは、可変構造体のために `MutableTangent` を返します。`MutableTangent` は実験的な機能です。したがって、`StructuralTangent`（直接 `Tangent` ではなく）の使用も実験的です。この通知が残っている間は、ChainRulesCore の任意の *マイナー* バージョンで動作やインターフェースに変更がある可能性があります。

