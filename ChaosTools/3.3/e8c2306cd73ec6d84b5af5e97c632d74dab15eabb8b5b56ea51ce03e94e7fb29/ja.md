```
gali(ds::DynamicalSystem, T, k::Int; kwargs...) -> GALI_k, t
```

与えられた `k` に対して、時間 `T` までの $\text{GALI}_k$[^Skokos2007] を計算します。$\text{GALI}_k(t)$ と時間ベクトル $t$ を返します。

第三の引数は `gali` の次数を設定します。`gali` 関数は、`k` の偏差ベクトルを持つ [`TangentDynamicalSystem`](@ref) を単純に初期化し、以下のメソッドを呼び出します。これは、自動ヤコビアンがデフォルトで使用されることを意味します。手動でヤコビアンをコーディングしている場合は、手動で [`TangentDynamicalSystem`](@ref) を初期化してください。

## キーワード引数

  * `threshold = 1e-12`: `GALI_k` が `threshold` を下回ると、反復が終了します。
  * `Δt = 1`: 偏差ベクトルの正規化間の時間ステップ。連続システムの場合、これは近似的です。
  * `u0`: システムの初期状態。デフォルトは `current_state(ds)` です。

## 説明

一般化アライメント指数、$\text{GALI}_k$ は、$D$ 次元ハミルトン系における混沌または規則的な挙動のタイプを示す効率的（かつ非常に高速な）指標です（$D$ は変数の数です）。$\text{GALI}_k(t)$ の*漸近的*な挙動は、初期条件から生じる軌道のタイプに重要に依存します。もしそれが混沌とした軌道であれば、

$$
\text{GALI}_k(t) \sim
\exp\left[\sum_{j=1}^k (\lambda_1 - \lambda_j)t \right]
$$

ここで、$\lambda_j$ は `j` 番目のリャプノフ指数です（[`lyapunov`](@ref)、[`lyapunovspectrum`](@ref) を参照）。一方、軌道が規則的であれば、$1 \le d \le D/2$ の $d$ 次元トーラス内の動きに対応し、次のようになります。

$$
\text{GALI}_k(t) \sim
    \begin{cases}
      \text{const.}, & \text{if} \;\; 2 \le k \le d  \; \; \text{and}
      \; \;d > 1 \\
      t^{-(k - d)}, & \text{if} \;\;  d < k \le D - d \\
      t^{-(2k - D)}, & \text{if} \;\;  D - d < k \le D
    \end{cases}
$$

伝統的に、$\text{GALI}_k(t)$ が `T` まで `threshold` より小さくならない場合、与えられた軌道は混沌としていると言われ、そうでなければ規則的です。

私たちの実装は、元の論文に基づいているのではなく、むしろ[^Skokos2016b] に記載された方法に基づいており、これは $A$ の特異値の積を使用します。ここで、$A$ は偏差ベクトルを*列*として持つ行列です。

[^Skokos2007]: Skokos, C. H. *et al.*, Physica D **231**, pp 30–54 (2007)

[^Skokos2016b]: Skokos, C. H. *et al.*, *Chaos Detection and Predictability* - Chapter 5 (section 5.3.1 and ref. [85] therein), Lecture Notes in Physics **915**, Springer (2016)
