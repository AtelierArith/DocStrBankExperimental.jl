```
NonmonotoneLinesearch(; kwargs...)
NonmonotoneLinesearch(M::AbstractManifold; kwargs...)
```

バーリザイ—ボルウェインステップサイズを使用した非単調線形探索を表すファンクタ [IannazzoPorcelli:2017](@cite)。

このメソッドはまず次を計算します。

(x -> p, F-> f)

$$
y_{k} = \operatorname{grad}f(p_{k}) - \mathcal T_{p_k←p_{k-1}}\operatorname{grad}f(p_{k-1})
$$

および

$$
s_{k} = - α_{k-1} ⋅ \mathcal T_{p_k←p_{k-1}}\operatorname{grad}f(p_{k-1}),
$$

ここで $α_{k-1}$ は前回の反復で計算されたステップサイズであり、$\mathcal T_{⋅←⋅}$ はベクトル輸送です。次に、バーリザイ—ボルウェインステップサイズは

$$
α_k^{\text{BB}} = \begin{cases}   \min(α_{\text{max}}, \max(α_{\text{min}}, τ_{k})), & \text{if} ⟨s_{k}, y_{k}⟩_{p_k} > 0,\\\\    α_{\text{max}}, & \text{else,}\end{cases}
$$

ここで

$$
τ_{k} = \frac{⟨s_{k}, s_{k}⟩_{p_k}}{⟨s_{k}, y_{k}⟩_{p_k}},
$$

直接戦略が選択された場合、または

$$
τ_{k} =  \frac{⟨s_{k}, y_{k}⟩_{p_k}}{⟨y_{k}, y_{k}⟩_{p_k}},
$$

逆戦略または交互戦略の場合の2つの間の交互に選択されます。次に、最小の $h = 0, 1, 2, …$ を見つけます。

$$
f(\operatorname{retr}_{p_k}(- σ^h α_k^{\text{BB}} \operatorname{grad}f(p_k)))  ≤
\max_{1 ≤ j ≤ \max(k+1,m)} f(p_{k+1-j}) - γ σ^h α_k^{\text{BB}} ⟨\operatorname{grad}F(p_k), \operatorname{grad}F(p_k)⟩_{p_k},
$$

ここで $σ ∈ (0,1)$ はステップ長の減少因子であり、$m$ は関数値が現在のものよりも低くなる必要がある反復の数で、$γ ∈ (0,1)$ は十分な減少パラメータです。最後に、ステップサイズは次のように計算されます。

$$
α_k = σ^h α_k^{\text{BB}}.
$$

# キーワード引数

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 中間結果を格納するための多様体 $\mathcal M$ 上の点
  * `p=allocate_result(M, rand)`: 中間結果を格納するため
  * `initial_stepsize=1.0`: 探索を開始するためのステップサイズ
  * `memory_size=10`: コスト値が現在のものよりも低くなる必要がある反復の数
  * `bb_min_stepsize=1e-3`: ゼロより大きいバーリザイ—ボルウェインステップサイズの下限
  * `bb_max_stepsize=1e3`: 最小ステップサイズより大きいバーリザイ—ボルウェインステップサイズの上限
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収縮 $\operatorname{retr}$、[再収縮に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `strategy=direct`: 新しいステップサイズが `:direct`、`:indirect` または `:alternating` 戦略を使用して計算されるかどうかを定義
  * `storage=`[`StoreStateAction`](@ref)`(M; store_fields=[:Iterate, :Gradient])`: `:Iterate` と `:Gradient` のために [`StoreStateAction`](@ref) を使用して効率を向上させる。
  * `stepsize_reduction=0.5`: 区間 $(0,1)$ に含まれるステップサイズ減少因子
  * `sufficient_decrease=1e-4`: 区間 $(0,1)$ に含まれる十分な減少パラメータ
  * `stop_when_stepsize_less=0.0`: 停止する際の最小ステップサイズ（前の最後のものが取られる）
  * `stop_when_stepsize_exceeds=`[`max_stepsize`](@ref)`(M, p)`): 注入半径を超えないように停止する際の最大ステップサイズ
  * `stop_increasing_at_step=100`: ステップサイズを増加させる最後のステップ（フェーズ1）
  * `stop_decreasing_at_step=1000`: ステップサイズを減少させる最後のステップサイズ（フェーズ2）

```
