# 勾配降下法

## コンストラクタ

```julia
GradientDescent(; alphaguess = LineSearches.InitialHagerZhang(),
linesearch = LineSearches.HagerZhang(),
P = nothing,
precondprep = Returns(nothing),
manifold = Flat())
```

キーワードは、ラインサーチと前処理の選択を制御するために使用されます。

## 説明

`GradientDescent` メソッドは、単純な勾配降下アルゴリズムであり、探索方向は現在の反復点での負の勾配であり、その後、ラインサーチステップを使用して最終ステップを計算します。このアプローチの説明については、Nocedal と Wright (ch. 2.2, 1999) を参照してください。

## 参考文献

  * Nocedal, J. and Wright, S. J. (1999), Numerical optimization. Springer Science 35.67-68: 7.
