`is_function_basis(::Type{F})`

`is_function_basis(f::F)`

引数（値または型）が*関数基*であるかどうかをテストし、以下のインターフェースをサポートします：

  * [`domain`](@ref) ドメインを照会するためのもの、
  * [`dimension`](@ref) 次元のためのもの、
  * [`basis_at`](@ref) 関数評価のためのもの、
  * [`grid`](@ref) コレクションポイントを取得するためのもの。
  * `length` および `getindex` 多変量基に対して `(domain_kind(domain(basis)) == :multivariate)`、getindex は互換性のある周辺基を返します。

[`linear_combination`](@ref) および [`collocation_matrix`](@ref) もサポートされており、上記に基づいて構築されます。

型（推奨）と値（便利のため）両方で使用できます。
