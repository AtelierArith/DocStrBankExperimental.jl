```
Job(spatial_setup, time_solver; kwargs...)
```

パラダイナミックシミュレーションに必要なすべての情報を含む型です。シミュレーションを開始するために `Job` を [`submit`](@ref) できます。

# 引数

  * `spatial_setup`: [`Body`](@ref) または [`MultibodySetup`](@ref)。
  * `time_solver`: [`VelocityVerlet`](@ref) または [`DynamicRelaxation`](@ref)。

# キーワード

  * `path::String`: 結果を保存するためのパス。まだ存在しない場合は、シミュレーション中に作成されます。（オプション）
  * `freq::Int`: 結果ファイルの出力頻度。`freq` 番目のタイムステップごとに出力ファイルが書き込まれます。（デフォルト: `10`）
  * `fields`: 出力ファイルにエクスポートするフィールド。許可されるキーワードは、選択した材料モデルによって異なります。ボディを作成する際に指定した材料のドキュメントを参照してください。（デフォルト: `(:displacement, :damage)`）

    `spatial_setup` が **`Body`** の場合、`fields` キーワードは次の形式を取ることができます：

      * `fields::Symbol`: 単一の出力フィールドを指定するシンボル。
      * `fields::NTuple{N,Symbol} where N`: 複数の出力フィールドを指定するタプル。
      * `fields::Vector{Symbol}`: 複数の出力フィールドを指定するベクター。

    `spatial_setup` が **`MultibodySetup`** の場合、`fields` キーワードは各ボディごとに別々に指定することもできます：

      * `fields::Dict{Symbol,T}`: 各ボディごとにフィールドを別々に含む辞書。`T` はここで単一のボディに使用できる `fields` キーワードのすべての可能な型です。

!!! note "ファイルエクスポートなし"
    `Job` を作成する際にキーワードが指定されていない場合、ファイルはエクスポートされません。


# 例

```julia-repl
julia> job = Job(multibody_setup, verlet_solver; path="my_results/sim1")
Job:
  spatial_setup  25880-point MultibodySetup
  time_solver    VelocityVerlet(n_steps=2000, safety_factor=0.7)
  options        export_allowed=true, freq=10
```
