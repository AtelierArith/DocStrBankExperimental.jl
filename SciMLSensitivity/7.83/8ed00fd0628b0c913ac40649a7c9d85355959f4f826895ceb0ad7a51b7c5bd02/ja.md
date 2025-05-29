```julia
ForwardDiffSensitivity{CS, CTS} <: AbstractForwardSensitivityAlgorithm{CS, Nothing, Nothing}
```

ForwardDiff.jlを通じた離散的な前方感度分析の実装です。逆モード自動微分環境内での隣接微分（すなわちZygoteを介して）で使用されると、`solve`呼び出しの前方微分が引き起こされます。

## コンストラクタ

```julia
ForwardDiffSensitivity(; chunk_size = 0, convert_tspan = nothing)
```

## キーワード引数

  * `chunk_size`: ジャコビアンを計算するためにForwardDiffが使用するチャンクサイズ、すなわち同時に計算される列の数。
  * `convert_tspan`: 時間を`Dual`値に変換するかどうか。デフォルトでは`nothing`で、コールバックが見つかった場合にのみ変換されます。コールバック（ハイブリッド方程式）を正確に微分するためには変換が必要です。

## SciMLProblemサポート

この`sensealg`は、ソルバーアルゴリズムが`SciMLBase.isautodifferentiable`である限り、任意の`SciMLProblem`をサポートします。`convert_tspan=true`のときのみ、`ForwardDiffSensitivity`はコールバックを正確に微分できます。
