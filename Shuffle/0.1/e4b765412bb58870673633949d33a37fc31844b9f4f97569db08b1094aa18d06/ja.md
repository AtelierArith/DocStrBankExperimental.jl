```
AbstractShuffle
```

[`AbstractDeterministicShuffle`](@ref) と [`AbstractRandomShuffle`](@ref) のスーパタイプです。

# 実装

新しいシャッフルアルゴリズムタイプは、[`AbstractDeterministicShuffle`](@ref) または [`AbstractRandomShuffle`](@ref) のいずれかのサブタイプであるべきです。アルゴリズムがインプレースで定義できる場合、[`shuffle!`](@ref) のみを拡張する必要があります。[`shuffle`](@ref)、[`nshuffle`](@ref)、および [`nshuffle!`](@ref) は、必要に応じてコピーを作成したり、[`shuffle!`](@ref) を繰り返し呼び出したりします。アルゴリズムがインプレースで定義できない場合は、[`shuffle`](@ref) と [`nshuffle!`](@ref) を定義します。[`nshuffle`](@ref) はコピーを作成し、[`nshuffle!`](@ref) を呼び出します。
