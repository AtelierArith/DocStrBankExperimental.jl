```
make_point_variable_ref(write_model::Union{InfiniteModel, JuMP.Model},
                        ivref::GeneralVariableRef,
                        support::Vector{Float64}
                        )::GeneralVariableRef
```

無限変数/導関数 `ivref` のための点変数を `support` で作成し、`write_model` に追加して `GeneralVariableRef` を返します。これは、[`expand_measure`](@ref) を介して生成された点変数のための内部メソッドです。これは、拡張オプティマイザーモデルを記述し、`InfiniteModel` を変更することなく測度を拡張したい人にも便利です。そのような場合、`write_model` はオプティマイザーモデルであり、点変数のために [`add_point_variable`](@ref add_point_variable(::JuMP.Model, ::Any, ::Any, ::Any)) を適切に拡張する必要があります。`write_model` がオプティマイザーモデルであり、`add_point_variable` が適切に拡張されていない場合はエラーが発生します。

これは無限パラメータ関数にも対応しており、その場合、無限パラメータ関数はサポートを入力として呼び出されます。
