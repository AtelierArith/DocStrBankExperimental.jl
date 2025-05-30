# 共役勾配降下法

## コンストラクタ

```julia
ConjugateGradient(; alphaguess = LineSearches.InitialHagerZhang(),
linesearch = LineSearches.HagerZhang(),
eta = 0.4,
P = nothing,
precondprep = Returns(nothing),
manifold = Flat())
```

厳密に正の定数 $eta$ は次のステップ方向を決定するために使用され、ここでのデフォルトは元の論文で使用されたもの（$0.01$）から逸脱しています。詳細については、以下の元の論文を参照してください。

## 説明

`ConjugateGradient` メソッドは Hager と Zhang (2006) および Hager と Zhang (2013) の要素を実装しています。デフォルトの `linesearch` は LineSearches.jl の `HagerZhang` です。このラインサーチは Hager と Zhang (2006) で提案されたものと正確に一致します。

## 参考文献

  * W. W. Hager と H. Zhang (2006) アルゴリズム 851: CG_DESCENT, 確実な降下を伴う共役勾配法。ACM Transactions on Mathematical Software 32: 113-137.
  * W. W. Hager と H. Zhang (2013), 限定メモリ共役勾配法。SIAM Journal on Optimization, 23, pp. 2150-2168.
