```
kalman_filter(y, T, R, C, Q, Z, D, E, s_0 = AbstractVector(), P_0 = Matrix();
    outputs = [:loglh, :pred, :filt], Nt0 = 0)

kalman_filter(regime_indices, y, Ts, Rs, Cs, Qs, Zs, Ds, Es,
    s_0 = AbstractVector(), P_0 = Matrix(); outputs = [:loglh, :pred, :filt],
    Nt0 = 0)
```

この関数は、次の状態空間モデルのカルマンフィルタを実装します：

```
s_{t+1} = C + T*s_t + R*ϵ_t    (遷移方程式)
y_t     = D + Z*s_t + u_t      (測定方程式)

ϵ_t ∼ N(0, Q)
u_t ∼ N(0, E)
Cov(ϵ_t, u_t) = 0
```

### 入力

  * `y`: `Ny` x `Nt` 行列で、データ `y_1, ... , y_T` を含む
  * `s_0`: オプションの `Ns` x 1 初期状態ベクトル
  * `P_0`: オプションの `Ns` x `Ns` 初期状態共分散行列

**メソッド 1 のみ:**

  * `T`: `Ns` x `Ns` 状態遷移行列
  * `R`: `Ns` x `Ne` 行列で、遷移方程式においてショックを状態にマッピングする
  * `C`: `Ns` x 1 定数ベクトルで、遷移方程式における
  * `Q`: `Ne` x `Ne` ショック共分散の行列
  * `Z`: `Ny` x `Ns` 行列で、測定方程式において状態を観測可能なものにマッピングする
  * `D`: `Ny` x 1 定数ベクトルで、測定方程式における
  * `E`: `Ny` x `Ny` 測定誤差共分散の行列

**メソッド 2 のみ:**

  * `regime_indices`: 長さ `n_regimes` の `AbstractVector{UnitRange{Int}}` で、`regime_indices[i]` はレジーム `i` の時間期間 `t` を示す
  * `Ts`: 各レジームのための `T` 行列の `AbstractVector{Matrix{S}}`
  * `Rs`
  * `Cs`
  * `Qs`
  * `Zs`
  * `Ds`
  * `Es`

ここで：

  * `Nt`: データがある時間期間の数
  * `Ns`: 状態の数
  * `Ne`: ショックの数
  * `Ny`: 観測可能なものの数

### キーワード引数

  * `outputs`: 計算して返す出力を指定する `[:loglh, :pred, :filt]` の一部。常に同じ数の戻り値があるが、例えば `:pred` が `outputs` に含まれていない場合、`s_pred` と `P_pred` は空の配列として返される
  * `Nt0`: すべての戻り値から省略するプレサンプル期間の数

### 出力

  * `loglh`: 条件付き対数尤度 P(y*t | y*{1:t-1}) の長さ `Nt` ベクトル
  * `s_pred`: 1ステップ予測状態ベクトル s_{t|t-1} の `Ns` x `Nt` 行列
  * `P_pred`: 予測状態ベクトルの平均二乗誤差 P_{t|t-1} の `Ns` x `Ns` x `Nt` 配列
  * `s_filt`: フィルタリングされた状態ベクトル s_{t|t} の `Ns` x `Nt` 行列
  * `P_filt`: フィルタリングされた状態ベクトルの平均二乗誤差 P_{t|t} を含む `Ns` x `Ns` x `Nt` 行列
  * `s_0`: `Ns` x 1 初期状態ベクトル。`Nt0 > 0` の場合、これは最後のプレサンプル状態ベクトルに再割り当てされている可能性がある
  * `P_0`: `Ns` x `Ns` 初期状態共分散行列。`Nt0 > 0` の場合、これは最後のプレサンプル状態共分散に再割り当てされている可能性がある
  * `s_T`: 最終フィルタリングされた状態 `s_{T|T}` の `Ns` x 1
  * `P_T`: 最終フィルタリングされた状態共分散行列 `P_{T|T}` の `Ns` x `Ns`

### 注意事項

`s_0` と `P_0` が省略されると、`init_stationary_states` を使用して計算されます。
