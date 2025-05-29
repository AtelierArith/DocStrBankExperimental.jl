```
ExperimentalSeasonalNaive(y::Vector{<:Real}, seasonal::Int; S::Int = 10_000)
```

季節的なナイーブモデルで、hステップ先の予測はSシナリオのシミュレーションの平均です。

$$
y_{T+h|T} = y_{T + h - m(k+1)} + \varepsilon_t
$$

ここで、mは季節周期、kは(h-1)/mの整数部分、$\varepsilon_t$はサンプリングされた誤差です。

実験的と呼ぶのは、これまでのところ良い参考文献や実装を見つけられなかったからです。何か知っていることがあれば、問題として投稿してください。
