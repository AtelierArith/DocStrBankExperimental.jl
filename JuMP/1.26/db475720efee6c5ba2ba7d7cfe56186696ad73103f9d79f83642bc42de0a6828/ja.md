```
read_from_file(
    filename::String;
    format::MOI.FileFormats.FileFormat = MOI.FileFormats.FORMAT_AUTOMATIC,
    kwargs...,
)
```

`filename` から `format` 形式の JuMP モデルを読み込みます。

サポートされている形式のリストについては、[`MOI.FileFormats.FileFormat`](@ref) を参照してください。

## キーワード引数

他の `kwargs` は、選択した形式の `Model` コンストラクタに渡されます。

詳細については、各ファイル形式の `Model` コンストラクタのドキュメントを参照してください。例えば、[`MOI.FileFormats.MPS.Model`](@ref)。

## 非線形モデル

後方互換性を維持するために、`.mof.json` および `.nl` ファイルの非線形モデルは [`MOI.NLPBlock`](@ref) に解析されます。[`MOI.ScalarNonlinearFunction`](@ref) として解析するには、キーワード `use_nlp_block = false` を渡してください。

## 圧縮

ファイル名が `.gz` で終わる場合、ファイルは GZip を使用して解凍されます。

ファイル名が `.bz2` で終わる場合、ファイルは BZip2 を使用して解凍されます。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> @objective(model, Min, log(x));

julia> filename = joinpath(mktempdir(), "model.mof.json");

julia> write_to_file(model, filename)

julia> new_model = read_from_file(filename; use_nlp_block = false)
A JuMP Model
├ solver: none
├ objective_sense: MIN_SENSE
│ └ objective_function_type: NonlinearExpr
├ num_variables: 1
├ num_constraints: 1
│ └ VariableRef in MOI.GreaterThan{Float64}: 1
└ Names registered in the model: none

julia> print(new_model)
Min log(x)
Subject to
 x ≥ 0
```
