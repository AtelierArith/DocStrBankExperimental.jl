```
abstract type AbstractKernelMatrix{T} <: AbstractMatrix{T}
```

カーネル関数 `f`、ターゲット要素 `X`、およびソース要素 `Y` を通じて表現される抽象行列のインターフェース。行列のエントリ `i,j` は `f(X[i],Y[j])` によって与えられます。具体的なサブタイプは少なくとも次を実装する必要があります。

```
`Base.getindex(K::AbstractKernelMatrix,i::Int,j::Int)`
```

`getindex(K,I::UnitRange,I::UnitRange)`、`getindex(K,I::UnitRange,j::Int)` および `getindex(adjoint(K),I::UnitRange,j::Int)` のより効率的な実装が利用可能な場合（例：SIMDベクトル化を使用）、そのようなメソッドを実装することで [`HMatrix`](@ref) の組み立て速度を向上させることができます。
