```
NonmonotoneLinesearch <: Linesearch
```

非単調線探索を表すファンクタで、Barzilai-Borweinステップサイズを使用します [IannazzoPorcelli:2017](@cite)。勾配降下アルゴリズムと組み合わせることで、この線探索は非単調線探索を伴うリーマンのBarzilai-Borwein（RBBNMLS）アルゴリズムを表します。各反復において、この線探索はまず次を見つけます。

$$
y_{k} = \operatorname{grad}F(x_{k}) - \operatorname{T}_{x_{k-1} → x_k}(\operatorname{grad}F(x_{k-1}))
$$

および

$$
s_{k} = - α_{k-1} * \operatorname{T}_{x_{k-1} → x_k}(\operatorname{grad}F(x_{k-1})),
$$

ここで、$α_{k-1}$は前回の反復で計算されたステップサイズであり、$\operatorname{T}$はベクトル輸送です。次に、Barzilai—Borweinステップサイズは次のようになります。

$$
α_k^{\text{BB}} = \begin{cases}
\min(α_{\text{max}}, \max(α_{\text{min}}, τ_{k})),  & \text{if } ⟨s_{k}, y_{k}⟩_{x_k} > 0,\\
α_{\text{max}}, & \text{else,}
\end{cases}
$$

ここで

$$
τ_{k} = \frac{⟨s_{k}, s_{k}⟩_{x_k}}{⟨s_{k}, y_{k}⟩_{x_k}},
$$

直接戦略が選択された場合、

$$
τ_{k} = \frac{⟨s_{k}, y_{k}⟩_{x_k}}{⟨y_{k}, y_{k}⟩_{x_k}},
$$

逆戦略の場合、そして交互戦略の場合はその2つの間で交互に行います。次に、次の条件を満たす最小の$h = 0, 1, 2, …$を見つけます。

$$
F(\operatorname{retr}_{x_k}(- σ^h α_k^{\text{BB}} \operatorname{grad}F(x_k)))
\leq
\max_{1 ≤ j ≤ \min(k+1,m)} F(x_{k+1-j}) - γ σ^h α_k^{\text{BB}} ⟨\operatorname{grad}F(x_k), \operatorname{grad}F(x_k)⟩_{x_k},
$$

ここで、$σ$はステップ長の減少因子 $∈ (0,1)$、$m$は関数値が現在のものよりも低くなる必要がある反復の数、$γ$は十分な減少パラメータ $∈(0,1)$です。次に、新しいステップサイズを次のように見つけます。

$$
α_k = σ^h α_k^{\text{BB}}.
$$

# フィールド

  * `initial_stepsize`:        (`1.0`) 探索を開始するためのステップサイズ
  * `memory_size`:             (`10`) 現在のコスト値よりも低くなる必要がある反復の数
  * `bb_min_stepsize`:         (`1e-3`) ゼロより大きいBarzilai-Borweinステップサイズの下限
  * `bb_max_stepsize`:         (`1e3`) min_stepsizeより大きいBarzilai-Borweinステップサイズの上限
  * `retraction_method`:       (`ExponentialRetraction()`) 使用する再収縮
  * `strategy`:                (`direct`) 新しいステップサイズが直接、間接、または交互戦略を使用して計算されるかどうかを定義
  * `storage`:                 (for `:Iterate` and `:Gradient`) a [`StoreStateAction`](@ref)
  * `stepsize_reduction`:      (`0.5`) 区間(0,1)に含まれるステップサイズ減少因子
  * `sufficient_decrease`:     (`1e-4`) 区間(0,1)に含まれる十分な減少パラメータ
  * `vector_transport_method`: (`ParallelTransport()`) 使用するベクトル輸送方法

内部使用のために

  * `candidate_point`:           (`allocate_result(M, rand)`) 中間結果を格納するため

さらに、次のフィールドは安全装置として機能します。

  * `stop_when_stepsize_less:     (`0.0`) 停止する際の最小ステップサイズ（前の最後のものが取られる）
  * `stop_when_stepsize_exceeds`: ([`max_stepsize`](@ref)`(M, p)`) 停止する際の最大ステップサイズ。
  * `stop_increasing_at_step`:    (^100`) ステップサイズを増加させる最後のステップ（フェーズ1）、
  * `stop_decreasing_at_step`:    (`1000`) ステップサイズを減少させる最後のステップサイズ（フェーズ2）、

`debug=`に`:Messages`を渡すと、これらが発生したときに`@info`が表示されます。

# コンストラクタ

```
NonmonotoneLinesearch()
```

フィールドの順序をオプション引数として（非推奨）。これは、デフォルトと候補のメモリ割り当てが線探索が動作する多様体を考慮していないため、非推奨です。

```
NonmonotoneLinesearch(M)
```

フィールドをキーワード引数として、再収縮とベクトル輸送がそれぞれ`M`のデフォルトのものに設定されます。

コンストラクタは非単調線探索を実行するファンクタを返します。 ```
