```
processes_to_coupledodes(processes [, default]; kw...)
```

与えられた `Vector` のプロセスを `DynamicalSystem`、特に `CoupledODEs` に変換します。すべてのプロセスは、ModelingToolkit.jl によって管理される記号方程式を表します。`default` は、`processes` に導入された「プロセスなし」変数が取得するデフォルトプロセスのベクトルです。構造的に簡略化される前に MTK モデルを取得するには [`processes_to_mtkmodel`](@ref) を使用してください。`processes` が何であるかの詳細については、[`processes_to_mtkmodel`](@ref) を参照するか、オンラインの [Tutorial](@ref) を参照してください。

## キーワード引数

  * `diffeq`: `CoupledODEs` を構築する際に DifferentialEquations.jl ODE 解法に渡されるオプション。
  * `inplace`: 動的システムがインプレースであるかどうか。システムの次元が ≤ 5 の場合はデフォルトで `true` になります。
  * `split = false`: ModelingToolkit.jl に従ってパラメータを分割するかどうか。デフォルトは ModelingToolkit のデフォルトではなく、すなわち分割は行われません。これは、すべてのパラメータが同じ型であると仮定して、パラメータアクセスを加速します。
  * `kw...`: その他のすべてのキーワードは `processes_to_mtkmodel` に伝播されます。

```
