```
koopman_smoother(y, T, R, C, Q, Z, D, E, s_0, P_0, s_pred, P_pred;
    Nt0 = 0)

koopman_smoother(regime_indices, y, Ts, Rs, Cs, Qs, Zs, Ds, Es,
    s_0, P_0, s_pred, P_pred; Nt0 = 0)
```

これは、S.J. Koopmanの「Disturbance Smoother for State Space Models」（Biometrika, 1993）に基づくカルマン平滑化プログラムであり、DurbinとKoopmanの「A Simple and Efficient Simulation Smoother for State Space Time Series Analysis」（Biometrika, 2002）で指定されています。

他のカルマン平滑化プログラムとは異なり、ムーア・ペンローズ擬似逆行列（`pinv`）を使用して特異行列を反転する必要がないため、効率の向上と反転問題の減少が期待できます。また、状態ベクトルと対応する行列は、ショックの革新を含むように拡張する必要がありません。代わりに、それらは自動的に`ϵ_smth`行列に保存されます。

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
  * `s_0`: `Ns` x 1の初期状態ベクトル
  * `P_0`: `Ns` x `Ns`の初期状態共分散行列
  * `s_pred`: カルマンフィルタからの1ステップ予測状態ベクトル`s_{t|t-1}`の`Ns` x `Nt`行列
  * `P_pred`: 予測状態ベクトルの平均二乗誤差`P_{t|t-1}`の`Ns` x `Ns` x `Nt`配列

**メソッド1のみ:** 状態空間システム行列`T`、`R`、`C`、`Q`、`Z`、`D`、`E`。`?kalman_filter`を参照してください。

**メソッド2のみ:** 各レジームの`regime_indices`およびシステム行列`Ts`、`Rs`、`Cs`、`Qs`、`Zs`、`Ds`、`Es`。`?kalman_filter`を参照してください。

ここで：

  * `Nt`: データがある期間の数
  * `Ns`: 状態の数
  * `Ne`: ショックの数
  * `Ny`: 観測可能な数

### キーワード引数

  * `Nt0`: 0より大きい場合、返される平滑化された状態とショックの行列は、その数の列（先頭から取得）だけ短くなります。

### 出力

  * `s_smth`: 平滑化された状態`s_{t|T}`の`Ns` x `Nt`行列
  * `ϵ_smth`: 平滑化されたショック`ϵ_{t|T}`の`Ne` x `Nt`行列

```
