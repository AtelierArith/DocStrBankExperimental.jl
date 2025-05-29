```
material!(body, set_name; kwargs...)
material!(body; kwargs...)
```

`body`の点に材料ポイントパラメータを割り当てます。`set_name`が指定されていない場合、パラメータはボディのすべての点に設定されます。

# 引数

  * `body::AbstractBody`: [`Body`](@ref).
  * `set_name::Symbol`: このボディのポイントセットの名前。

# キーワード

許可されるキーワードは、選択した材料モデルによって異なります。ボディを作成する際に指定した材料のドキュメントを参照してください。デフォルトの材料キーワードは次のとおりです。

材料パラメータ:

  * `horizon::Float64`: ポイント相互作用の半径。
  * `rho::Float64`: 密度。

弾性パラメータ:

  * `E::Float64`: ヤング率。
  * `nu::Float64`: ポアソン比。
  * `G::Float64`: 剪断弾性率。
  * `K::Float64`: 体積弾性率。
  * `lambda::Float64`: 1番目のラメパラメータ。
  * `mu::Float64`: 2番目のラメパラメータ。

破壊パラメータ:

  * `Gc::Float64`: 臨界エネルギー放出率。
  * `epsilon_c::Float64`: 臨界ひずみ。

!!! note "弾性パラメータ"
    材料を指定するには、正確に2つの弾性パラメータが必要です。


!!! note "破壊パラメータ"
    シミュレーションで破壊を有効にするには、許可された破壊パラメータの1つを定義してください。定義されていない場合、破壊は無効になります。


# 例外

  * ボディ材料の指定に適さないkwargがある場合はエラーが発生します。

# 例

```julia-repl
julia> material!(body; horizon=3.0, E=2.1e5, rho=8e-6, Gc=2.7)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`
  1 point parameter(s):
    Parameters BBMaterial: δ=3.0, E=210000.0, nu=0.25, rho=8.0e-6, Gc=2.7
```
