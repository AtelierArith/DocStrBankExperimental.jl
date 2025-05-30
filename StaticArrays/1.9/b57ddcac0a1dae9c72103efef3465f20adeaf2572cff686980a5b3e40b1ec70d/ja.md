```
SHermitianCompact{N, T, L} <: StaticMatrix{N, N, T}
```

[`StaticArray`](@ref) のサブタイプで、エルミート行列を表すことができます。`LinearAlgebra.Hermitian`とは異なり、`SHermitianCompact`は行列の下三角部分のみを（`SVector`として）格納し、対角成分は実数でない場合があります。下三角部分は列優先順序で格納され、上対角成分は転置された下対角成分の `adjoint` です。対角成分はそのまま返されます。例えば、`SHermitianCompact{3}`の場合、格納された要素のインデックスは次のように視覚化できます：

```
┌ 1 ⋅ ⋅ ┐
| 2 4 ⋅ |
└ 3 5 6 ┘
```

型パラメータ：

  * `N`: 行列の次元；
  * `T`: 下三角部分の要素型；
  * `L`: 下三角要素を格納する `SVector` の長さ。

`L` は常に `N` 番目の [三角数](https://en.wikipedia.org/wiki/Triangular_number) です。

`SHermitianCompact` は次のいずれかから構築できます：

  * 下三角要素を含む `AbstractVector` から；
  * 列優先順序で上三角および下三角要素を含む `Tuple` から；または
  * 別の `StaticMatrix` から。

後者の2つの場合、下三角要素のみが使用され、上三角要素は無視されます。

要素型が実数の場合、`SHermitianCompact` はエルミートかつ対称です。そうでない場合、`SHermitianCompact` 行列 `a` が `LinearAlgebra.ishermitian` に従ってエルミートであることを保証するには、`(a+a')/2` のようにその随伴と平均を取るか、`LinearAlgebra.Hermitian(a)` を使ってデータのエルミートビューを取ります。ただし、後者のケースはコンパクトストレージを使用するようには特化されていません。
