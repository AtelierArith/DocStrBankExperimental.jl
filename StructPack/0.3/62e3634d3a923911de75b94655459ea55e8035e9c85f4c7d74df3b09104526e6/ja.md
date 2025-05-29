[`VectorFormat`](@ref)の修正。

アンパック中、将来のエントリの型とフォーマットは、[`iterstate`](@ref)のオーバーロードを介して過去のエントリに依存する場合があります。

!!! info
    [`DynamicVectorFormat`](@ref)は、[`iterstate`](@ref)がインデックスを列挙するだけであっても、現在は[`VectorFormat`](@ref)よりも遅くなっています。しかし、原則として、コンパイラはこの場合に[`DynamicVectorFormat`](@ref)を最適化するために必要なすべての情報を持っているはずであり、パフォーマンスを同等に引き上げることができます。将来的には、[`DynamicVectorFormat`](@ref)を非推奨にし、その機能を[`VectorFormat`](@ref)に統合する可能性があります。

