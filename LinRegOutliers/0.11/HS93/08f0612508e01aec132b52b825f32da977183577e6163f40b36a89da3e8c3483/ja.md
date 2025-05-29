```
hs93initialset(setting)
```

与えられた回帰設定に対して、Hadi & Simonoff (1993) アルゴリズムの最初の部分を実行します。返されるインデックスの配列は、回帰パラメータの数を p としたときのクリーンなサブセットの長さ p + 1 のインデックスです。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つ RegressionSetting オブジェクト。

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> hs93initialset(reg0001)
3-element Array{Int64,1}:
 4
 3
 5
```

# 参考文献

Hadi, Ali S., and Jeffrey S. Simonoff. "Procedures for the identification of multiple outliers in linear models." Journal of the American Statistical Association 88.424 (1993): 1264-1272.
