```
objective_owf(wm::AbstractWaterModel)
```

最適な水流（owf）問題の仕様に対する目的を設定します。デフォルトでは、（1）各貯水池からの水をある体積流量で抽出することに関連するコストと（2）事前に定義された電気料金で電力を消費するポンプ操作に関連するコストを最小化します。つまり、目的は

$$
\text{minimize} ~ \sum_{t \in \mathcal{T}^{\prime}} \Delta t
\left(\left[\sum_{(i, j) \in \mathcal{P}_{t}} \pi_{ijt} P_{ijt}\right] +
\left[\sum_{i \in \mathcal{R}_{t}} \mu_{it} q_{it}\right]\right),
$$

ここで、$\mathcal{T}^{\prime} := \mathcal{T} \setminus \{T\}$は、最終的なタンクの体積を計算するためだけに予約された最後の時間インデックスを除いた時間インデックスの集合です；$\Delta t$は時間$t$と時間$t + 1$を接続する時間ステップです；$\mathcal{P}_{t}$は時間$t$に操作可能なポンプの集合です；$\pi_{ijt}$はポンプ$(i, j)$および時間$t$でのポンピングに使用される電気の価格（エネルギー単位あたりのコスト）です；$P_{ijt}$は時間$t$におけるポンプ$(i, j)$の電力消費です；$\mathcal{R}_{t}$は時間$t$に利用可能な貯水池の集合です；$\mu_{it}$は時間$t$に貯水池$i$から1体積単位の水を抽出（および処理）するコストです；$q_{it}$は時間$t$に貯水池$i$から抽出される水の体積流量です。
