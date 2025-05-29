```
hs93basicsubset(setting, initialindices)
```

与えられた回帰設定に対して、Hadi & Simonoff (1993) アルゴリズムの第2部を実行します。返されるインデックスの配列は、クリーンなサブセットのインデックスであり、その長さ h は観測数の半分以上である必要があります。h は (n + p - 1) / 2 の整数部分に設定されます。

# 引数

  * `setting::RegressionSetting`: フォーミュラとデータセットを持つ RegressionSetting オブジェクト。
  * `initialindices::Array{Int, 1}`: クリーンな観測の (p + 1) サブセット。

# 例

```julia-repl
julia> reg0001 = createRegressionSetting(@formula(calls ~ year), phones);
julia> initialsetindices = hs93initialset(reg0001)
3-element Array{Int64,1}:
 4
 3
 5
 julia> hs93basicsubset(reg0001, initialsetindices)
12-element Array{Int64,1}:
  5
  9
 10
  3
  6
  4
  7
 22
 11
  8
 12
 13
```

# 参考文献

Hadi, Ali S., and Jeffrey S. Simonoff. "Procedures for the identification of multiple outliers in linear models." Journal of the American Statistical Association 88.424 (1993): 1264-1272.
