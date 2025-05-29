```
build_nn_function(eqs, nn, soutput)
```

出力に依存する実行可能な関数を構築します。結果として得られる `built_function` は次のように呼び出されます：

```julia
built_function(input, output, ps)
```

また、これを [`build_nn_function(::EqT, ::AbstractSymbolicNeuralNetwork)`](@ref) と比較してください。

# 拡張ヘルプ

[`build_nn_function(::EqT, ::AbstractSymbolicNeuralNetwork)`](@ref) の *拡張ヘルプセクション* を参照してください。
