```
outlknn(X; metric = :eucl, k, algo = sum, scal::Bool = false)
outlknn!(X::Matrix; metric = :eucl, k, algo = sum, scal::Bool = false)
```

ローカルkNN距離ベースの外れ値度を計算します。

  * `X` : Xデータ (n, p)。

キーワード引数:

  * `metric` : 距離を計算するために使用されるメトリック。関数 `getknn` を参照してください。
  * `k` : 考慮する最近傍の数。
  * `algo` : 最近傍への `k` 距離を要約する関数。
  * `scal` : ブール値。`true` の場合、外れ値度を計算する前に `X` の各列がスケーリングされます。

このアイデアは、観測値のKNN外れ値度をその近隣のKNN外れ値度と比較し、外れ値度のローカルな測定を提供することです。各観測値（`X` の行）について、外れ値度は次のように定義されます：

  * 観測値とその `k` 最近傍との間の距離の要約（例えば、合計）が計算され、out1と呼ばれます。
  * 観測値の `k` 最近傍の各々について同じ要約が計算され、返された `k` の値の平均が計算され、out2と呼ばれます。
  * 最後に、観測値の外れ値度は比 out1 / out2 として定義されます。

このアプローチは、ローカル外れ値因子（LOF）法（Breunig et al. 2000）の簡略化として見ることができ、ローカル密度がk距離の逆数によって推定される簡略化LOF法（Schubert et al 2014 p.206, Campos et al. 2016 p.896）に似ています。

## 参考文献

Campos, G.O., Zimek, A., Sander, J., Campello, R.J.G.B., Micenková, B., Schubert, E., Assent, I., Houle, M.E., 

2016. 教師なし外れ値検出の評価に関する研究：測定、データセット、および実証研究。データマイニングと知識発見 30, 891–927. https://doi.org/10.1007/s10618-015-0444-8

Schubert, E., Zimek, A., Kriegel, H.-P., 2014. ローカル外れ値検出の再考：空間、ビデオ、ネットワーク外れ値検出への応用に関する局所性の一般化された見解。データマイニングと知識発見 28, 190–237.  https://doi.org/10.1007/s10618-012-0300-z

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "octane.jld2")
@load db dat
X = dat.X
wlst = names(X)
wl = parse.(Float64, wlst)
n, p = size(X)
## サンプルのうち6つ（25, 26, および 36-39）は添加されたアルコールを含んでいます。
s = [25; 26; 36:39]
typ = zeros(Int, n)
typ[s] .= 1
#plotsp(X, wl; xlabel = "波長 (nm)", ylabel = "吸光度").f

metric = :eucl ; k = 15 ; algo = maximum
#algo = :maximum
res = outlknn(X; metric, k, algo) ;
@names res
f, ax = plotxy(1:n, res.d, typ, xlabel = "観測値インデックス", ylabel = "外れ値度")
text!(ax, 1:n, res.d; text = string.(1:n), fontsize = 10)
f

nlv = 3
model = pcasph(; nlv)
fit!(model, X)
T = model.fitm.T
metric = :eucl 
k = 15
res = outlknn(T; metric, k, scal)
plotxy(1:n, res.d, typ, xlabel = "観測値インデックス", ylabel = "外れ値度").f
```
