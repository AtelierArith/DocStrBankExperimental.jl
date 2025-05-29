```
connect(output_connector, ap_name::Symbol, input_connector; verbose = true)
connect(output_connector, ap::AnalysisPoint, input_connector; verbose = true)
```

`output_connector` と `input_connector` をその間に [`AnalysisPoint`](@ref) を挟んで接続します。受信接続 `output_connector` は出力コネクタであることが期待されます（例えば、 `ModelingToolkitStandardLibrary.Blocks.RealOutput`）、逆もまた然りです。

*注意*: 接続は *因果的* であると仮定されており、つまり

```julia
@named P = FirstOrder(k = 1, T = 1)
@named C = Gain(; k = -1)
connect(C.output, :plant_input, P.input)
```

は正しいですが、

```julia
connect(P.input, :plant_input, C.output)
```

は通常は正しくありません（モデルが逆モデルでない限り）。

# 引数

  * `output_connector`: 出力コネクタ
  * `input_connector`: 入力コネクタ
  * `ap`: 明示的に作成された [`AnalysisPoint`](@ref)
  * `ap_name`: 名前が指定された場合、指定された名前の [`AnalysisPoint`](@ref) が自動的に作成されます。

# キーワード引数

  * `verbose`: 入力が出力に接続されている場合（逆因果関係）に警告します。この警告は逆モデルを分析している場合は無視されます。
