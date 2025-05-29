```
plot_Nyquist(a;label)
```

ナイキストプロットを作成します

# 引数

  * `a::Circuit`: ナイキストプロットに追加する回路
  * `label`: プロットのためのキーワード引数ラベル

# 例

```julia
julia> using EISAnalysis
julia> eval(initialize());
julia> circuit1 = r-r/c;
julia> circuit2 = r-r/q;
julia> plot_Nyquist(circuit1,circuit2;label= ["R-C Circuit","R-CPE Circuit"]);
```
