```
AbstractLieGroup{𝔽, O<:AbstractGroupOperation, M<:AbstractManifold{𝔽}} <: AbstractManifold{𝔽}
```

リー群を表すための抽象型です。ほとんどの場合、[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) と [`AbstractGroupOperation`](@ref) を「組み合わせる」ことで十分です。詳細は [`LieGroup`](@ref) を参照してください。
