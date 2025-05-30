注意: Juliaでは、閉じた抽象型を2つの異なるシステムで表現できます。

1. Union{Type1, Type2}を使用する
2. すべての型定義が抽象型レベルにある標準の抽象型を使用する

（具体的な型に対してのみ関数を定義すると、推論エンジンは将来別の具体的な型が存在するかもしれないと仮定するため、奇妙なことが起こります）

# アプローチ 1.

利点: 具体的な型の定義を提供することは、実際には型推論に十分です。コードの再利用が増えます。欠点: `Dict(:a => Some(1), :b => None())` のような型推論は、`Dict{Symbol, Any}` を推論する代わりに `Dict{Symbol, Union{Some, None}}` を推論します。

これに関する内部の詳細は、多くの場合、`Base.promote_typejoin(type1, type2)` が共通の型を導き出すために使用されることです。この型階層が使用される一方で、無関係な2つの型の `Base.promote_typejoin` は常に `Any` になります。

`Dict(:a => Identity(1), :b => nothing) isa Dict{Symbol, Option{Int}}` をサポートするために、`promote_typejoin` をオーバーロードする必要があります。

# アプローチ 2.

利点: `Dict(:a => Some(1), :b => None())` は実際に `Dict{Symbol, Option}` を推論します。欠点: 常に封印された型に固有の別々の関数で機能を最初に実装し、その後、`genericfunction(o::Option) = optionfunction(o)` を介して一般的な関数を特定のものに指し示すように注意する必要があります。

`Union` に対して `promote_typejoin` が意図した通りに機能するように管理できたので、私たちはアプローチ 1 に従い、はるかに高いコード再利用とデータ型再利用を可能にします。
