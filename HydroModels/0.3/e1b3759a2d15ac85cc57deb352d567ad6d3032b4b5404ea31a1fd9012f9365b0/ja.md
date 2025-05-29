```
(flux::UnitHydrograph)(input::AbstractArray, pas::ComponentVector; kwargs...)
```

入力時系列にユニットハイドログラフ畳み込みを適用します。

# 引数

  * `input::AbstractArray{T,D}`: 入力データ。形状は `(variables, timesteps)` (D=2) または `(variables, nodes, timesteps)` (D=3) です。
  * `pas::ComponentVector`: ユニットハイドログラフ関数 (`uh_func`) のパラメータ。

# キーワード引数

  * ( `:DISCRETE` ソルバーの場合): `solver`, `timeidx`, `interp`。
  * (3D入力の場合): ノードへのマッピングパラメータ `ptyidx`。

# 戻り値

  * `AbstractArray`: ルーティングされた出力で、形状は入力の時間（およびノード、D=3の場合）次元に一致します: `(output_variables, timesteps)` または `(output_variables, nodes, timesteps)`。

# 例

```julia
# 'uh' が UnitHydrograph インスタンスであると仮定
routed_flow = uh(input_runoff, parameters)
```

# 注意事項

  * 挙動は、構築時に設定された `solvetype` (`:DISCRETE` または `:SPARSE`) に依存します。
  * `:DISCRETE` はODEソルバーアプローチを使用します（`solver` kwargが必要）。
  * `:SPARSE` はスパース行列を介して直接畳み込みを使用します。
  * 3D入力は `ptyidx` を必要とし、内部的に各ノードごとに2Dメソッドを呼び出します。
  * 単一時点入力（ベクトル）はサポートされていません。
