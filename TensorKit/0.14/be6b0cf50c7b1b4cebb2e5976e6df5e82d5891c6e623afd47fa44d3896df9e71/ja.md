```
const Rep
```

`G<:Group` のグループの型を持つ `Rep[G]` として使用されるシングルトン型の定数で、`D` を指定することなく具体的な型 `GradedSpace{Irrep[G],D}` のインスタンスを構築または取得するために使用されます。`Rep[G] == Vect[Irrep[G]]` であることに注意してください。

関連情報として [`Irrep`](@ref) と [`Vect`](@ref) を参照してください。
