```
K, γ, info = glover_mcfarlane_2dof(G::AbstractStateSpace{Continuous}, Tref::AbstractStateSpace{Continuous}, γ = 1.1, ρ = 1.1;
W1 = 1, Wo = I, match_dc = true, kwargs...)
```

フィードバックとフィードフォワード補償器の共同設計

$$
K = \begin{bmatrix} K_1 & K_2 \end{bmatrix}
$$

```
   ┌──────┐   ┌──────┐        ┌──────┐    ┌─────┐
r  │      │   │      │        │      │    │     │
──►│  Wi  ├──►│  K1  ├───+───►│  W1  ├───►│  G  ├─┐y
   │      │   │      │   │    │      │    │     │ │
   └──────┘   └──────┘   │    └──────┘    └─────┘ │
                         │                        │
                         │    ┌──────┐            │
                         │    │      │            │
                         └────┤  K2  ◄────────────┘
                              │      │
                              └──────┘
```

返されるコントローラー `K` は、測定ベクトル `[r; y]`（正のフィードバック）を受け取り、すなわち、すべてのブロック `Wi, K1, K2, W1` を含みます。`match_dc = true` の場合、`Wi` は静的ゲインが `Tref` と正確に一致するように自動的に計算されます。そうでない場合、`Wi` は `I` に設定されます。`info` という名前のタプルには、フィードフォワードフィルターが含まれており、検査のために使用されます（`info.K1 = K1*Wi`）。

# 引数:

  * `G`: プラントモデル
  * `Tref`: 参照モデル
  * `γ`: 相対 γ
  * `ρ`: 設計パラメータ、通常 1 < ρ < 3。ロバスト性を犠牲にしてモデルマッチングを強調するために増加させます。
  * `W1`: ループシェーピング用のプレ補償器。
  * `Wo`: 出力選択行列。制御変数よりも測定値が多い場合、この行列を使用して制御する測定値を選択できます。
  * `kwargs`: [`hinfsynthesize`](@ref) に送信されます。

参照: Skogestad の「Multivariable Feedback Control: Analysis and Design」の第9.4.3節。この参考文献には、設計されたコントローラーを推定状態からのフィードバックを持つオブザーバーとしてゲインスケジューリング実装に関する貴重な指針が含まれています。`W1` にインテグレータが含まれている場合にアンチワインドアップ保護を得るために、`W1` を自己条件付きハヌス形式に変換し（[`hanus`](@ref) を使用）、コントローラーを次のように実装します。

```julia
W1h = hanus(W1)             # 外部ループを実行

# 各イテレーション
us = filter(Ks, [r; y])     # info.Ks を通して入力をフィルタリング（フィルタは伝達関数を適用する架空の関数）
u  = filter(W1h, [us; ua])  # us と u-actual（入力飽和後）を W1h でフィルタリング
ua = clamp(u, lower, upper) # 次のイテレーションのために u の飽和値として ua を計算
```

# 例:

```@example
using RobustAndOptimalControl, Plots
P = tf([1, 5], [1, 2, 10]) # プラント
W1 = tf(1,[1, 0]) |> ss    # ループシェーピングコントローラー

Tref = tf(1, [1, 1])^2 |> ss # 参照モデル（できれば P と同じ次数）

K1dof, γ1, info1 = glover_mcfarlane(ss(P), 1.1; W1)
K2dof, γ2, info2 = glover_mcfarlane_2dof(ss(P), Tref, 1.1, 1.1; W1)

G1 = feedback(P*K1dof)
G2 = info2.Gcl

w = exp10.(LinRange(-2, 2, 200))
bodeplot(info2.K1, w, lab="フィードフォワードフィルタ")
plot([step(G1, 15), step(G2, 15), step(Tref, 15)], lab=["1-DOF" "2-DOF" "Tref"])
```
