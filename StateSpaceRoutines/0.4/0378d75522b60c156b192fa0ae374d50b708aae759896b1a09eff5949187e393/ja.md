```
carter_kohn_smoother(y, T, R, C, Q, Z, D, E, s_0, P_0;
    Nt0 = 0, draw_states = true)

carter_kohn_smoother(regime_indices, y, Ts, Rs, Cs, Qs,
    Zs, Ds, Es, s_0, P_0; Nt0 = 0, draw_states = true)
```

このプログラムは、CarterとKohnの「On Gibbs Sampling for State Space Models」（Biometrika, 1994）に基づくシミュレーションスムーザーです。これは、時間tの状態の条件付き分布から、時間t+1から時間Tまでの観測値と状態の完全なセットを考慮して再帰的にサンプリングします。Durbin-Koopmanシミュレーションスムーザーとは異なり、これはMoore-Penrose擬似逆行列を使用して潜在的に特異な行列を反転することに依存します。

状態空間はショックで拡張され（`?augment_states_with_shocks`を参照）、拡張された状態空間はカルマンフィルタリングおよびスムージングされます。最後に、スムーズされた状態とショックは拡張された状態ベクトルからインデックス化されます。

ショックで拡張する前の元の状態空間は次のように与えられます：

```
s_{t+1} = C + T*s_t + R*ϵ_t    (遷移方程式)
y_t     = D + Z*s_t + u_t      (測定方程式)

ϵ_t ∼ N(0, Q)
u_t ∼ N(0, E)
Cov(ϵ_t, u_t) = 0
```

### 入力

  * `y`: データ `y_1, ... , y_T` を含む `Ny` x `Nt` 行列
  * `s_0`: `Ns` x 1 初期状態ベクトル
  * `P_0`: `Ns` x `Ns` 初期状態共分散行列

**メソッド1のみ:** 状態空間システム行列 `T`, `R`, `C`, `Q`, `Z`, `D`, `E`。 `?kalman_filter` pp を参照 **メソッド2のみ:** `regime_indices` および各レジームのシステム行列 `Ts`, `Rs`, `Cs`, `Qs`, `Zs`, `Ds`, `Es`。 `?kalman_filter` を参照

ここで：

  * `Nt`: データがある期間の数
  * `Ns`: 状態の数
  * `Ne`: ショックの数
  * `Ny`: 観測値の数

### キーワード引数

  * `Nt0`: 0より大きい場合、返されるスムーズされた状態とショックの行列は、その数の列（先頭から取得）だけ短くなります
  * `draw_states`: スムーズされた状態を分布 `N(s_{t|T}, P_{t|T})` から描画するか、平均 `s_{t|T}` を使用するかを示します（Hamiltonスムーザーに減少）

### 出力

  * `s_smth`: スムーズされた状態 `s_{t|T}` の `Ns` x `Nt` 行列
  * `ϵ_smth`: スムーズされたショック `ϵ_{t|T}` の `Ne` x `Nt` 行列

```
