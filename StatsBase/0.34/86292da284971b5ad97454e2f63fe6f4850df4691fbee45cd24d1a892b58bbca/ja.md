```
eweights(t::AbstractArray{<:Integer}, λ::Real; scale=false)
eweights(t::AbstractVector{T}, r::StepRange{T}, λ::Real; scale=false) where T
eweights(n::Integer, λ::Real; scale=false)
```

過去の観測値に指数的に減少する重みを割り当てる[`Weights`](@ref)ベクトルを構築します（`t`内の大きな整数値`i`）。整数値`n`は考慮する過去の観測値の数を表します。`n`は、`t`のみが渡され、要素が整数である場合、`maximum(t) - minimum(t) + 1`にデフォルト設定され、スーパーセット範囲`r`も渡された場合は`length(r)`にデフォルト設定されます。`t`の代わりに`n`が明示的に渡された場合、`t`は`1:n`にデフォルト設定されます。

`scale`が`true`の場合、`t`内の各要素`i`に対して重みの値は次のように計算されます：

$$
(1 - λ)^{n - i}
$$

`scale`が`false`の場合、各値は次のように計算されます：

$$
λ (1 - λ)^{1 - i}
$$

# 引数

  * `t::AbstractVector`: 時間インデックスまたはタイムスタンプ
  * `r::StepRange`: タイムスタンプのサブセットから重みを構築する際に使用する大きな範囲
  * `n::Integer`: 考慮する過去のイベントの数
  * `λ::Real`: スムージングファクターまたはレートパラメータで、$0 < λ ≤ 1$。この値が0に近づくと、結果の重みはほぼ等しくなり、1に近い値はベクトルの尾の要素により大きな重みを置きます。

# キーワード引数

  * `scale::Bool`: 重みを0と1の間にスケーリングして返す（デフォルト：false）

# 例

```jldoctest
julia> eweights(1:10, 0.3; scale=true)
10-element Weights{Float64, Float64, Vector{Float64}}:
 0.04035360699999998
 0.05764800999999997
 0.08235429999999996
 0.11764899999999996
 0.16806999999999994
 0.24009999999999995
 0.3429999999999999
 0.48999999999999994
 0.7
 1.0
```

# リンク

  * [https://en.wikipedia.org/wiki/Moving*average#Exponential*moving_average](https://en.wikipedia.org/wiki/Moving_average#Exponential_moving_average)
  * [https://en.wikipedia.org/wiki/Exponential_smoothing](https://en.wikipedia.org/wiki/Exponential_smoothing)

```
