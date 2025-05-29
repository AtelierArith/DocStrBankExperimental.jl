```
fitted_params(mach)
```

`fit!`された機械`mach`の学習されたパラメータを返します。例えば、線形モデルの係数などです。

これは名前付きタプルであり、可能であれば人間が読みやすい形式です。

`mach`が、パイプライン構文`model1 |> model2 |> ...`を使用して構築された複合モデルのための機械である場合、返される名前付きタプルは複合型のフィールド名をキーとして持ちます。対応する値は、そのモデルにバインドされた基礎となる学習ネットワーク内の機械のフィッティングされたパラメータです。（複数の機械が同じモデルを共有している場合、値はベクトルになります。）

```julia-repl
julia> using MLJ
julia> @load LogisticClassifier pkg=MLJLinearModels
julia> X, y = @load_crabs;
julia> pipe = Standardizer() |> LogisticClassifier();
julia> mach = machine(pipe, X, y) |> fit!;

julia> fitted_params(mach).logistic_classifier
(classes = CategoricalArrays.CategoricalValue{String,UInt32}["B", "O"],
 coefs = Pair{Symbol,Float64}[:FL => 3.7095037897680405, :RW => 0.1135739140854546, :CL => -1.6036892745322038, :CW => -4.415667573486482, :BD => 3.238476051092471],
 intercept = 0.0883301599726305,)
```

[`report`](@ref)も参照してください。
