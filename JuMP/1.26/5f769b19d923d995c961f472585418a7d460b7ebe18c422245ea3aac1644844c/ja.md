```
GenericNonlinearExpr{V}(head::Symbol, args::Vector{Any})
GenericNonlinearExpr{V}(head::Symbol, args::Any...)
```

スカラー値の非線形関数 `head(args...)` は、呼び出し演算子 `head` と `args` に順序付けられた引数を持つ象徴的な式ツリーとして表されます。

`V` は式に存在する [`AbstractVariableRef`](@ref) の型であり、JuMP 拡張のディスパッチを助けるために使用されます。

## `head`

`head::Symbol` はモデルによってサポートされている演算子でなければなりません。

サポートされている単変数演算子のデフォルトリストは次のように示されます：

  * [`MOI.Nonlinear.DEFAULT_UNIVARIATE_OPERATORS`](@ref)

サポートされている多変数演算子のデフォルトリストは次のように示されます：

  * [`MOI.Nonlinear.DEFAULT_MULTIVARIATE_OPERATORS`](@ref)

追加の演算子は [`@operator`](@ref) を使用して追加できます。

[`MOI.ModelLike`](@ref) によってサポートされている演算子の完全なリストは、[`MOI.ListOfSupportedNonlinearOperators`](@ref) 属性をクエリすることで確認できます。

## `args`

ベクトル `args` には非線形関数への引数が含まれています。演算子が単変数の場合、1つの要素を含む必要があります。それ以外の場合は、複数の要素を含むことができます。

`GenericNonlinearExpr{V}` のサブタイプである [`AbstractVariableRef`](@ref) の `V` に対して、各要素は次のいずれかでなければなりません：

  * 型 `<:Real` の定数値
  * `V`
  * [`GenericAffExpr{T,V}`](@ref)
  * [`GenericQuadExpr{T,V}`](@ref)
  * [`GenericNonlinearExpr{V}`](@ref)

ここで `T<:Real` かつ `T == value_type(V)` です。

## サポートされていない演算子

最適化ツールが `head` をサポートしていない場合、[`MOI.UnsupportedNonlinearOperator`](@ref) エラーがスローされます。

このエラーがスローされるタイミングについては保証がなく、モデルに関数が最初に追加されたときにスローされる場合もあれば、[`optimize!`](@ref) が呼び出されたときにスローされる場合もあります。

## 例

関数 $f(x) = sin(x)^2$ を表すには、次のようにします：

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> f = sin(x)^2
sin(x) ^ 2.0

julia> f = GenericNonlinearExpr{VariableRef}(
           :^,
           GenericNonlinearExpr{VariableRef}(:sin, x),
           2.0,
       )
sin(x) ^ 2.0
```
