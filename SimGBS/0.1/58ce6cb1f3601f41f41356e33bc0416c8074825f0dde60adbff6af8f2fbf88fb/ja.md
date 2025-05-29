```
digestGenome(genofile, re, useChr, useChrLen, lower ,upper, plotOutput, writeOutput)
```

制限酵素を使用して仮想消化を行い、GBSフラグメントを生成します。

この関数は、指定された制限酵素を使用してゲノムを消化し、したがってGBSフラグメントを生成します。フラグメントサイズ選択ステップも含まれています。

# 引数

  * `genofile`: 参照ゲノムを含むファイル
  * `re`: 使用する制限酵素
  * `useChr`: シミュレーションする染色体の番号またはセット
  * `useChrLen`: シミュレーションに使用する染色体の長さ（cM）、さもなくば全染色体を使用
  * `lower`: フラグメントサイズ選択の下限
  * `upper`: フラグメントサイズ選択の上限
  * `winSize`: 平均ゲノムカバレッジを計算するために使用されるウィンドウのサイズ
  * `plotOutput`: グラフィカル出力が必要な場合はtrueに設定
  * `writeOutput`: テキスト出力が必要な場合はtrueに設定

...

# 例

```julia
julia> digestGenome("ref.fa.gz", [SimGBS.ApeKI], [1], Array{Float64}(undef,0), 65 ,195, 1000000, false, true)
```
