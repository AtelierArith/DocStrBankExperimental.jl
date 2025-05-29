# `erdos_renyi_undirected`

無向Erdős-Rényiグラフを生成します。無向Erdős-Rényiグラフは、`n`ノード間の各無向エッジが確率`p`で存在するように生成されます。

入力が生成されたグラフの平均次数である別の呼び出し形式もあります。

**現在の実装はsprandを使用していますが、将来的には変更される可能性があります。** **バージョン間で信頼できる出力にこのルーチンに依存しないでください。**

## 入力

  * `n`: ノードの数
  * `p`: エッジの確率、または平均次数。 $`p` >= 1$ の場合、$`p`$ は確率ではなく平均次数として解釈されます。 ($`p`=1$ の確率でErdős-Rényiグラフを生成する意味はありません)
  * `d`: 希望する平均次数で、d/nを介して確率に変換されます。

## 関数

  * `erdos_renyi_undirected(n::Int,p::Float64)` 確率または平均次数を指定します
  * `erdos_renyi_undirected(n::Int,d::Int)` 平均次数を直接指定します

## 出力

  * Erdős-Rényiグラフのための行列ネットワークタイプ。

## 例

```
# 接続された位相転移を表示
n = 100
avgdegs = linspace(1.,2*log(n),100) 
compsizes = map( (dbar) -> 
        maximum(scomponents(erdos_renyi_undirected(n,dbar)).sizes),
    avgdegs )
using Plots
unicodeplots()
plot(avgdegs,compsizes,xaxis=("平均次数"),yaxis=("最大コンポーネントサイズ"))    
```
