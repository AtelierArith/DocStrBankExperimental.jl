```
selwold(indx, r; smooth = true, npoint = 5, alpha = .05, digits = 3, graph = true, 
    step = 2, xlabel = "インデックス", ylabel = "値", title = "スコア")
```

Woldの基準は、LVモデル（例：PLSR）の次元数を選択するためのものです。

  * `indx` : モデルパラメータを表す変数、例：PLSRモデルのLVの数。
  * `r` : エラー率のベクトル（n）、例：RMSECV。

キーワード引数：

  * `smooth` : ブール値。`true`の場合、選択はレートRの移動平均平滑化の後に行われます（関数`mavg`を参照）。
  * `npoint` : レートRを平滑化するために使用される移動平均のウィンドウ。
  * `alpha` : レートRのしきい値として使用されるプロポーションα。
  * `digits` : 出力の桁数。
  * `graph` : ブール値。`true`の場合、出力がプロットされます。
  * `step` : グラフのxticksを定義するために使用されるステップ。
  * `xlabel` : プロットの横ラベル。
  * `ylabel` : プロットの縦ラベル。
  * `title` : 左側のプロットのタイトル。

選択基準は「精度向上比率」です：

  * R = 1 - `r`(a+1) / `r`(a)

ここで、`r`はモデルのパフォーマンスを定量化する観測エラー率（例：RMSEP、分類エラー率など）であり、aはモデルの次元数（= LVの数）です。`r`はPCAの固有値など、他の指標を表すこともできます。

Rは、新しいLVがモデルに追加された後のパフォーマンス効率の相対的な向上を示します。Rがしきい値αよりも低くなるまで反復が続きます。デフォルトでは、指標としてデフォルトの`alpha`=.05が関数に設定されていますが、ユーザーはデータと簡潔性の目的に応じて他の値を設定する必要があります。

Wold（1978年；Bro et al. 2008も参照）は、交差検証された残差平方和の比率、すなわちPRESSとSSRの比率を使用しました。代わりに、関数`selwold`は、一貫した性質の値（入力ベクトル`r`の連続値）を比較します。たとえば、`r`はLi et al.（2002）およびAndries et al.（2011）でPRESS値に設定されており、これはWestad & Martens（2000）で説明されている「罰因子」と同等です。

比率Rは不安定になることがあり（特に`r`が識別モデルのエラー率である場合）、次元選択が難しくなります。そのような状況では、関数`selwold`はRの平滑化を計算することを提案します（引数`smooth`）。

この関数は、（プロットがある場合を除いて）2つの出力を返します：

  * `opt` : `r`の最小値に対応するインデックス。
  * `sel` : R（または平滑化されたR）しきい値からの選択のインデックス。

## 参考文献

Andries, J.V.M., Vander Heyden, Y., Buydens, L.M.C., 2011. 改良された部分最小二乗モデリングにおける変数削減に基づく予測特性ランク変数と部分最小二乗複雑性の適応。Analytica Chimica Acta 705, 292-305.  https://doi.org/10.1016/j.aca.2011.06.037

Bro, R., Kjeldahl, K., Smilde, A.K., Kiers, H.A.L., 2008. コンポーネントモデルの交差検証：現在の方法に対する批判的な視点。Anal Bioanal Chem  390, 1241-1251. https://doi.org/10.1007/s00216-007-1790-1

Li, B., Morris, J., Martin, E.B., 2002. 部分最小二乗回帰のためのモデル選択。Chemometrics and Intelligent Laboratory Systems 64, 79-89.  https://doi.org/10.1016/S0169-7439(02)00051-5

Westad, F., Martens, H., 2000. 部分最小二乗回帰における有意性テストに基づく近赤外分光法における変数選択。J. Near Infrared  Spectrosc., JNIRS 8, 117–124.

Wold S. 因子および主成分モデルにおける成分数の交差検証推定。Technometrics. 1978;20(4):397-405

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "cassav.jld2") 
@load db dat
@names dat
X = dat.X 
y = dat.Y.tbc
year = dat.Y.year
tab(year)
s = year .<= 2012
Xtrain = X[s, :]
ytrain = y[s]
Xtest = rmrow(X, s)
ytest = rmrow(y, s)
n = nro(Xtrain)

segm = segmts(n, 50; rep = 30)
model = plskern()
nlv = 0:20
res = gridcv(model, Xtrain, ytrain; segm, score = rmsep, nlv).res
res[res.y1 .== minimum(res.y1), :]
plotgrid(res.nlv, res.y1;xlabel = "LVの数", ylabel = "RMSEP").f
zres = selwold(res.nlv, res.y1; smooth = true, graph = true) ;
@show zres.opt
@show zres.sel
zres.f
```
