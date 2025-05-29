```
make_semi_infinite_variable_ref(write_model::Union{InfiniteModel, JuMP.Model},
                                ivref::GeneralVariableRef,
                                indices::Vector{Int},
                                values::Vector{Float64}
                                )::GeneralVariableRef
```

無限変数/導関数/パラメータ関数 `ivref` のための半無限変数を `support` に作成し、`write_model` に追加して `GeneralVariableRef` を返します。これは、[`expand_measure`](@ref) を介して測度を拡張することによって生成される半無限変数のための内部メソッドです。これは、拡張オプティマイザーモデルを記述し、`InfiniteModel` を変更することなく測度を拡張したい人々にも便利です。そのような場合、`write_model` はオプティマイザーモデルであり、[`add_semi_infinite_variable`](@ref add_semi_infinite_variable(::JuMP.Model, ::Any, ::Any)) は半無限変数のために適切に拡張されるべきです。`write_model` がオプティマイザーモデルであり、`add_semi_infinite_variable` が適切に拡張されていない場合はエラーが発生します。これは、現在 `InfiniteModel.optimizer_model` に保存されているオプティマイザーモデルのためのものであることに注意してください。
