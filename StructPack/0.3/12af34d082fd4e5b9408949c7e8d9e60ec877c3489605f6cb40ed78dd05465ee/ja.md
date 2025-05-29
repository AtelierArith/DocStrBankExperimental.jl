[`MapFormat`](@ref)の修正。

アンパック中、将来のエントリの型とフォーマットは、[`iterstate`](@ref)のオーバーロードを介して過去のエントリに依存する場合があります。

!!! info
    [`DynamicMapFormat`](@ref)は現在、[`MapFormat`](@ref)よりも遅く、たとえ[`iterstate`](@ref)がインデックスを列挙するだけであっても、原則としてコンパイラはこの場合に[`DynamicMapFormat`](@ref)を最適化するために必要なすべての情報を持っているはずです。将来的には、[`DynamicMapFormat`](@ref)を非推奨にし、その機能を[`MapFormat`](@ref)に統合する可能性があります。

