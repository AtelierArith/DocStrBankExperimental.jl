```
koopman_disturbance_smoother(y, T, R, Q, Z, D, E, s_pred, P_pred;
    Nt0 = 0, output = [:states, :obs])

koopman_smoother(regime_indices, y, Ts, Rs, Qs, Zs, Ds, Es,
    s_pred, P_pred; Nt0 = 0)
```

この擾乱スムーザーは、S.J. Koopmanの「Disturbance Smoother for State Space Models」（Biometrika, 1993）からの状態スムーザー`koopman_smoother`と共に使用することを意図しています。これは、DurbinとKoopmanの「A Simple and Efficient Simulation Smoother for State Space Time Series Analysis」（Biometrika, 2002）で指定されています。

状態空間は次のように与えられます：

```
s_{t+1} = C + T*s_t + R*ϵ_t    (遷移方程式)
y_t     = D + Z*s_t + u_t      (測定方程式)

ϵ_t ∼ N(0, Q)
u_t ∼ N(0, E)
Cov(ϵ_t, u_t) = 0
```

### 入力

  * `y`: データ`y_1, ... , y_T`を含む`Ny` x `Nt`行列
  * `s_pred`: 一ステップ予測状態ベクトル`s_{t|t-1}`（カルマンフィルタから）の`Ns` x `Nt`行列
  * `P_pred`: 予測状態ベクトルの平均二乗誤差`P_{t|t-1}`の`Ns` x `Ns` x `Nt`配列

**メソッド1のみ:** 状態空間システム行列`T`、`R`、`Q`、`Z`、`D`、`E`。`?kalman_filter`を参照してください。

**メソッド2のみ:** 各レジームの`regime_indices`とシステム行列`Ts`、`Rs`、`Qs`、`Zs`、`Ds`、`Es`。`?kalman_filter`を参照してください。

ここで：

  * `Nt`: データがある期間の数
  * `Ns`: 状態の数
  * `Ne`: ショックの数
  * `Ny`: 観測可能な数

### キーワード引数

  * `Nt0`: 0より大きい場合、返されるスムーズな擾乱とショック行列は、その数の列だけ短くなります（先頭から取得）。
  * `obs_disturbance`: trueの場合、遷移方程式と測定方程式の両方の擾乱を返します。そうでない場合は、遷移方程式の擾乱のみが返されます。

### 出力

  * `s_dist`: 遷移方程式の擾乱`r_t`の`Ns` x `Nt`行列
  * `y_dist`: 測定方程式の擾乱`e_t`の`Ny` x `Nt`行列
