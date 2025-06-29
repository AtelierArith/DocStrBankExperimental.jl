```julia
ArrayPartition(x::AbstractArray...)
```

`ArrayPartition` `A` は、異なる配列 `A.x` で構成される配列です。これらは単一の配列のようにインデックス付けされますが、各サブ配列は異なる型を持つ場合があります。しかし、ブロードキャストは効率的にループするようにオーバーロードされているため、`A .+= 2.+B` はその計算において型安定です。たとえ `A.x[i]` と `A.x[j]` が型が一致しなくてもです。この配列型は、型安定なブロードキャストが必要な場合に標準の配列の代わりに使用できるように、完全な配列インターフェースが含まれています。1つの例は、[DifferentialEquations.jl](https://docs.sciml.ai/DiffEqDocs/stable/) の異種微分方程式です。

`ArrayPartition` は単一の配列のように動作します。`A[i]` は最初の配列をインデックスし、次に2番目の配列、などと線形に続きます。しかし、`A.x` は配列が格納されている場所です。したがって、次のように：

```julia
using RecursiveArrayTools
A = ArrayPartition(y, z)
```

私たちは `A.x[1]==y` および `A.x[2]==z` を持つことになります。`f.(A)` のようなブロードキャストは効率的です。
