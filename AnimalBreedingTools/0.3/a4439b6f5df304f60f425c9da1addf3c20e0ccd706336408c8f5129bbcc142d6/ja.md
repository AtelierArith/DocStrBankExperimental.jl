```
bentB = bending(B [, W], gamma=nothing, tol=eps, verbose=false)
bentB = bending(B, gamma=nothing, tol=eps, verbose=false)
```

対称行列 `B`（群間分散）に対して、別の対称行列 `W`（群内分散）を使用して、Hayes と Hill (1981) によって説明された従来の「曲げ」方法を適用します。結果の行列は `bentB = (1-gamma)*B + gamma*v*W` であり、ここで `v` は `B` の平均固有値で、`gamma` は 0 と 1 の間の定数で、ユーザーが提供するか、この関数によって生成されます。`W` が省略されると、代わりに単位行列が使用されます。

ユーザーが `gamma` を提供した場合、関数は単に曲げの公式を適用し、`bentB` が正定値であるかどうかを確認せずに `bentB` を返します。それ以外の場合（`gamma=nothing`）、この関数は `gamma=1/1000` を生成し、曲げを適用し、`bentB` が正定値である場合に `bentB` を返します（`minimum(eigen(bentB).values)>tol`、デフォルトの `tol` はマシンのイプシロンです）。そうでない場合、関数は `gamma=2/1000`、`gamma=3/1000`、...、および `gamma=1000/1000` を試し、`bentB` が正定値になるまで繰り返します。

`verbose=true` の場合、この関数は `v`（`B` の平均固有値）と曲げに使用された `gamma` を出力します（デフォルト: `verbose=false`）。
