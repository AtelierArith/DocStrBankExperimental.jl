```
DAR(y::Vector{Fl}, lags::Int) where Fl
```

動的自己回帰モデルは次のように定義されます：

$$
\begin{gather*}
    \begin{aligned}
        y_{t} &= \phi_0 + \sum_{i=1}^{lags} \phi_{i, t} y_{t - i} + \varepsilon_{t}  \quad \varepsilon_{t} \sim \mathcal{N}(0, \sigma^2_{\varepsilon})\\
        \phi_{i, t+1} &= \phi_{i, t} + \eta{i, t}  \quad \eta{i, t} \sim \mathcal{N}(0, \sigma^2_{i, \eta})\\
    \end{aligned}
\end{gather*}
$$

!!!! 注 システム行列     システム行列を構築する際、対応するタイムスタンプを尊重してすべてのシステム行列を構築するために、最初の `lags` 観測値を取り除きます。

!!! 警告 予測     動的自己回帰モデルにはまだ [`forecast`](@ref) メソッドが実装されていません。      このモデルで予測を行いたい場合は、問題をオープンしてください。

!!! 警告 欠損値     現在、動的自己回帰モデルは欠損値（`NaN` 観測値）をサポートしていません。

# 例

```jldoctest
julia> model = DAR(randn(100), 2)
DAR
```
