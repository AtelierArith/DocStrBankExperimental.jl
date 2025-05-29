# LBFGS

## コンストラクタ

```julia
LBFGS(; m::Integer = 10,
alphaguess = LineSearches.InitialStatic(),
linesearch = LineSearches.HagerZhang(),
P=nothing,
precondprep = Returns(nothing),
manifold = Flat(),
scaleinvH0::Bool = true && (typeof(P) <: Nothing))
```

`LBFGS` には、メモリの長さ `m` と `scaleinvH0` フラグの2つの特別なキーワードがあります。メモリの長さは、どれだけの過去のヘッセ行列の近似を保存するかを決定します。`scaleinvH0 == true` の場合、逆ヘッセ行列を近似するための二重ループ再帰における初期推定は、Nocedal と Wright (第2版) (sec. 7.2) に見られるようにスケーリングされた単位行列です。

さらに、LBFGS は `P` と `precondprep` キーワードを介して前処理をサポートしています。

## 説明

`LBFGS` メソッドは、Nocedal と Wright (sec. 7.2, 2006) に記載されている制限付きメモリ BFGS アルゴリズムを実装しており、Liu & Nocedal (1989) のオリジナル論文に基づいています。これは、過去の近似と勾配を使用してヘッセ行列の近似を更新する準ニュートン法です。

## 参考文献

  * Wright, S. J. and J. Nocedal (2006), Numerical optimization, 2nd edition. Springer
  * Liu, D. C. and Nocedal, J. (1989). "On the Limited Memory Method for Large Scale Optimization". Mathematical Programming B. 45 (3): 503–528
