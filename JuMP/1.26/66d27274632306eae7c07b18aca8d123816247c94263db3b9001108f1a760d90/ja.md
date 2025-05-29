```
@expression(model::GenericModel, expression)
@expression(model::GenericModel, [index_sets...], expression)
@expression(model::GenericModel, name, expression)
@expression(model::GenericModel, name[index_sets...], expression)
```

効率的に式を構築して返します。

`name` 引数はオプションです。インデックスセットが渡されると、コンテナが構築され、式はインデックスセットのインデックスに依存する場合があります。

## キーワード引数

  * `container = :Auto`: `container = Array`、`container = DenseAxisArray`、`container = SparseAxisArray`、またはJuMP拡張によってサポートされている他の任意のコンテナタイプを渡すことで、コンテナタイプを強制します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:5]);

julia> @expression(model, shared, sum(i * x[i] for i in 1:5))
x[1] + 2 x[2] + 3 x[3] + 4 x[4] + 5 x[5]

julia> shared
x[1] + 2 x[2] + 3 x[3] + 4 x[4] + 5 x[5]
```

[`@variable`](@ref) と同様に、2番目の引数はインデックスセットを定義することができ、これらのインデックスは式の構築に使用できます：

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> @expression(model, expr[i = 1:3], i * sum(x[j] for j in 1:3))
3-element Vector{AffExpr}:
 x[1] + x[2] + x[3]
 2 x[1] + 2 x[2] + 2 x[3]
 3 x[1] + 3 x[2] + 3 x[3]
```

匿名構文もサポートされています：

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> expr = @expression(model, [i in 1:3], i * sum(x[j] for j in 1:3))
3-element Vector{AffExpr}:
 x[1] + x[2] + x[3]
 2 x[1] + 2 x[2] + 2 x[3]
 3 x[1] + 3 x[2] + 3 x[3]
```
