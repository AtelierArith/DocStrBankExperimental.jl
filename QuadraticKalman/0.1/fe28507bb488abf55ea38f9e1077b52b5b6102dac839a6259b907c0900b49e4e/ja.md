```
qkf_filter(data::QKData{T1,1}, model::QKModel{T,T2})
```

**二次カルマンフィルタ（QKF）**を長さ`T̄`の時系列に対して実行し、新しい結果配列のセットを返します（アウトオブプレース）。

# 説明

この関数は、`qkf_filter!`と同じ*二次*カルマンフィルタの再帰を実装していますが、配列をインプレースで更新する代わりに、予測、更新、および出力のための新しい配列を割り当てます。これは、`data`や`model`を変更したり再利用したりしたくない文脈で使用するのが簡単ですが、大規模な問題に対してはメモリ効率が悪くなる可能性があります。

各時間ステップで、次の処理を行います：

1. **状態予測**（`predict_Z_tt` / `predict_P_tt`）
2. **測定予測**（`predict_Y_tt` / `predict_M_ttm1`）
3. **カルマンゲイン計算**（`compute_K_t`）
4. **状態と共分散の更新**（`update_Z_tt`, `update_P_tt`）
5. **PSD補正**（`correct_Zₜₜ`）
6. **対数尤度**の計算。

# 引数

  * `data::QKData{T1,1}`   `qkf_filter!`と同じ構造で、フィールドは：

      * `Y::Vector{T1}`, `T̄::Int`, `M::Int`。
  * `model::QKModel{T,T2}`   `qkf_filter!`と同じパラメータ構造で、フィールドは：

      * `N::Int`, `P::Int`, `μ̃ᵘ, Σ̃ᵘ`など。

# 返り値

フィールドを持つ名前付きタプル：

  * `ll_t::Vector{Float64}`   各時間ステップの対数尤度（サイズ = `T̄`）。
  * `Z_tt::Array{T,3}`   各時間ステップでのフィルタリングされた状態（使用時の次元は`(T, P, T̄+1)`）。
  * `P_tt::Array{T,4}`   フィルタリングされた状態共分散配列。
  * `Y_ttm1::Vector{T}`   各ステップの予測測定。
  * `M_ttm1::Array{T,4}`   予測測定共分散。
  * `K_t::Array{T,4}`   各時間ステップのカルマンゲイン。
  * `Z_ttm1::Array{T,3}`   一歩先の予測状態。
  * `P_ttm1::Array{T,4}`   一歩先の予測共分散。

# 詳細

1. **初期化**：

      * `Z_tt`と`P_tt`のための新しい配列を作成し、初期状態を`aug_mean`と`aug_cov`に設定します。
2. **時間ループ**： 

      * **予測**：`predict_Z_tt`, `predict_P_tt`。
      * **測定**：`predict_Y_tt`, `predict_M_ttm1`。
      * **ゲインと更新**：`compute_K_t`, `update_Z_tt`, `update_P_tt`。
      * **補正**：PSDのための`correct_Z_tt`。
      * **尤度**：`compute_loglik`。
3. **インプレースの変更なし**：

      * 各ステップは新しい配列を返し、元の入力は変更されません。

# 例

```julia
data = QKData(Y, M=measurement_dim, T̄=length(Y)-1)
model = QKModel(...)
result = qkf_filter(data, model)

@show result.ll_t
@show result.Z_tt[:, end]   # 最終状態
```
