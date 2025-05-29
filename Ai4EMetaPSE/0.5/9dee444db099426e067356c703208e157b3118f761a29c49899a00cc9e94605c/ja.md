```julia
generatecode(
    io::AbstractString,
    type::Ai4EMetaPSE.jsonModel;
    write2File
) -> Ai4EMetaPSE.MetaSolution

```

jsonファイルを読み込み、[`MetaSolution`](@ref)型を返します。

  * `io`: Jsonファイル名またはjson文字列
  * `type`: jsonのタイプ、`CommonJson`、`ModelJson`など。
  * `write2File`: 生成されるスクリプトの名前、または何も指定しない場合。何も指定しない場合、スクリプトは生成されません。`デフォルト`: 何も指定しない

# 例:

```julia
str = """{
    "name": "Name",
    "pkgs": [
        "ModelingToolkit",
        "DifferentialEquations"
    ],
    "variables": [
        "x(t) = 1.0",
        "y(t) = 1.0",
        "z(t) = 2.0"
    ],
    "parameters": [
        "σ = 1.0",
        "ρ = 3.0",
        "β = 5.0" 
    ],
    "equations": [
        "der(x) = σ*(y - x)",
        "der(y) = x*(ρ - z) - y",
        "der(z) = x*y - β*z"
    ],
    "u0": [
        "x => 1.0",
        "y => 2.0",
        "z => 3.0"
    ],
    "timespan": [0,1,0.1],
    "solver": "Rosenbrock23"
}"""
solution = generatecode(str, CommonJson(); write2File="s.jl")
```
