```
l1tf(y, λ; α = 1e-2, β = 5e-1, μ = 2, MAXITER = 40, MAXLSITER = 20, atol = 1e-4, verbose = false)

内部点法を使用してL1トレンドフィルタリング問題の解を見つけます：
最小化 ``{\frac{1}{2}} \left\| y - x \right\|_{2}^{2} + \lambda \left\| D x \right\|_{1}``
ここで ``D`` は二次差分行列です。

実装は著者による元のMATLABコードに基づいています。

### オプション引数
- `α = 1e-2`: バックトラッキングラインサーチパラメータ (0,0.5]
- `β = 5e-1`: バックトラッキングラインサーチパラメータ (0,1)
- `μ = 2`: IPMパラメータ：tの更新
- `MAXITER = 40`: IPMパラメータ：IPMの最大反復回数
- `MAXLSITER = 20`: IPMパラメータ：ラインサーチの最大反復回数
- `atol = 1e-4`: IPMパラメータ：許容誤差

### 参考文献
- "l1 Trend Filtering", S. Kim, K. Koh, ,S. Boyd and D. Gorinevsky https://web.stanford.edu/~gorin/papers/l1_trend_filter.pdf#page=13.55
- https://web.stanford.edu/~boyd/l1_tf/
```
