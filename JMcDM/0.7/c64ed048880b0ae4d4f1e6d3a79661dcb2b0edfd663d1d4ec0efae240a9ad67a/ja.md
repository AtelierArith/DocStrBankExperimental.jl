```
    mcdm(df, w, fns, method)

与えられた意思決定行列、重みベクトル、および関数リストに対して選択した方法を実行します。
```

# 引数:

  * `df::Matrix`: 行列の型の n × m の意思決定行列。
  * `weights::Array{Float64, 1}`: 基準のための m 次元の重みベクトル。
  * `fs::Array{Function, 1}`: 各単一基準に対して最大化または最小化する m 次元の関数のベクトル。
  * `method::MCDMMethod`: 好ましい MCDMMethod。

# 説明

この方法は MCDMMethod 型のサブタイプの1つです。例を参照してください。

# 出力

  * `::MCDMResult`: MCDMResult 型のサブタイプから派生したオブジェクト。

# 例

```julia-repl

julia> subtypes(MCDMMethod)
23-element Vector{Any}:
 ArasMethod
 CocosoMethod
 CodasMethod
 CoprasMethod
 CriticMethod
 EdasMethod
 ElectreMethod
 GreyMethod
 LMAWMethod
 LOPCOWMethod
 MabacMethod
 MaircaMethod
 MarcosMethod
 MERECMethod
 MooraMethod
 MoosraMethod
 OCRAMethod
 PIVMethod
 PrometheeMethod
 PSIMethod
 ROVMethod
 SawMethod
 TopsisMethod
 VikorMethod
 WaspasMethod
 WPMMethod


julia> # mcdm() for Topsis:
julia> # mcdm(df, w, fns, TopsisMethod())

julia> # mcdm() for Saw:
julia> # mcdm(df, w, fns, SawMethod())

julia> # mcdm() with optional parameters:
julia> # mcdm(df, w, fns, GreyMethod(0.6))
```
