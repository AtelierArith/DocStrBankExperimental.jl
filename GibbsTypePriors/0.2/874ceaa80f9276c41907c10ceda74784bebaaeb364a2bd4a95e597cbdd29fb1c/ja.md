```
Pkn_NGG(k, n, β, σ)
```

k クラスターを取得するための事前確率質量を計算します。これは、直接計算または Cnk の再帰計算を使用して行うことができ、任意の精度で行えます。k の大きな値に対して安定していますが、k の小さな値に対しては不安定になる可能性があります。その場合、関数は警告を表示し、ギブス型プロセスの予測分布に基づく近似スキームを使用することになります (Bystrova, 2020)。

参考文献:

  * Bystrova, D, Kon Kam King, G, Deslandes, F, Arbel, J. ベイズ非パラメトリックモデルにおけるクラスターの事前分布の近似, 2020 (準備中)。

# 例

```julia-repl
julia> GibbsTypePriors.Pkn_NGG(10, 100, 1.2, 0.6)
```
