```
struct HomSpace{S<:ElementarySpace, P1<:CompositeSpace{S}, P2<:CompositeSpace{S}}
    codomain::P1
    domain::P2
end
```

型 `P1` のコドメインと型 `P2` のドメインを持つ写像の線形空間を表します。HomSpace は VectorSpace のサブタイプではないことに注意してください。つまり、後者は特定のカテゴリとそのオブジェクトを示すために制限され、HomSpace は区別されます。
