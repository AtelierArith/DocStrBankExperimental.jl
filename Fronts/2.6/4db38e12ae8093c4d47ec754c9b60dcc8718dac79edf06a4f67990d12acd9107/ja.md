```
solve(prob::DirichletProblem[, alg::BoltzmannODE; abstol, maxiters, d_dob_hint, verbose]) -> Solution
```

問題 `prob` を解きます。

# 引数

  * `prob`: 解くべき問題。
  * `alg=BoltzmannODE()`: 使用するアルゴリズム。

# キーワード引数

  * `abstol=1e-3`: 初期条件の絶対許容誤差。
  * `maxiters=100`: 最大反復回数。
  * `verbose=true`: 解決が失敗した場合に警告を出すかどうか。

# 参考文献

GERLERO, G. S.; BERLI, C. L. A.; KLER, P. A. 水平毛細管流の直接および逆解法のためのオープンソース高性能ソフトウェアパッケージ。Capillarity, 2023, vol. 6, no. 2, p. 31-40.

参照: [`Solution`](@ref), [`BoltzmannODE`](@ref)
