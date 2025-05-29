```
build_nn_function(eq, nn)
```

シンボリック方程式、シンボリック入力配列、および[`SymbolicNeuralNetwork`](@ref)に基づいて実行可能な関数を構築します。

この関数は次のように呼び出すことができます：

```julia
built_function(input, ps)
```

# 実装

内部的には、[`_build_nn_function`](@ref)を呼び出し、次にインデックス`k`を介して式を*並列化*します。

# 拡張ヘルプ

実装セクションで言及された関数は、発生した問題に対処するためにアドホックで調整されました。他の問題が発生する可能性があります。もし問題に遭遇した場合は、[githubで問題を開いてください](https://github.com/JuliaGNI/SymbolicNeuralNetworks.jl/issues)。
