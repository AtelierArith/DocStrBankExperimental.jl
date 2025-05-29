```
conf(pred, y; digits = 1)
```

混同行列。

  * `pred` : 単変量予測。
  * `y` : 単変量観測データ。

キーワード引数：

  * `digits` : パーセンテージを四捨五入するために使用される桁数。

## 例

```julia
using Jchemo, CairoMakie

y = ["d"; "c"; "b"; "c"; "a"; "d"; "b"; "d"; 
    "b"; "b"; "a"; "a"; "c"; "d"; "d"]
pred = ["a"; "d"; "b"; "d"; "b"; "d"; "b"; "d"; 
    "b"; "b"; "a"; "a"; "d"; "d"; "d"]
#y = rand(1:10, 200); pred = rand(1:10, 200)

res = conf(pred, y) ;
@names res
res.cnt       # カウント（`A`から構築されたデータフレーム） 
res.pct       # 行の%（`Apct`から構築されたデータフレーム）
res.A         
res.Apct
res.diagpct
res.accpct    # 精度（% 分類成功）
res.lev       # レベル

plotconf(res).f

plotconf(res; cnt = false, ptext = false).f
```
