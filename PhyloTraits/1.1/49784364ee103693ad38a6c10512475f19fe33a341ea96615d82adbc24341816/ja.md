```
descendencedataframe(net::HybridNetwork, which=:allhybrids; checkpreorder=true)
descendencedataframe(net::HybridNetwork, node::Vector{Node}; checkpreorder=true)
descendencedataframe(net::HybridNetwork, edge::Vector{Edge}; checkpreorder=true)
```

`net`内の各分類群が受け継いだゲノムの割合を含むデータフレーム。最初のメソッドではデフォルトで各ハイブリッドノードから、2番目と3番目のメソッドでは入力ベクター内の各ノードまたはエッジからのデータを含む。データフレームはネットワーク内の各ティップ（分類群）ごとに1行を持ち、以下の列を持つ：

  * 各エッジまたはノードごとに1列、列名は「shift*{edge*number}」のパターンに従い、`edge_number`は入力エッジまたはノードに関連付けられたエッジの番号（この場合、親エッジが使用される）
  * `tipnames`というラベルの付いた1つの追加列、ティップラベルを含む。

このデータフレーム内の`shift_*`列は、入力`edge`上のシフトや入力`node`の上にあるエッジに関連付けられた回帰ベクターとして使用できる。最後のメソッドで`which=:allhybrids`オプションを使用すると、各シフト列は`net`内のハイブリッドノードに関連付けられ、ハイブリッドノードの直下にあるエッジのシフトをモデル化する。これは超越的進化のテストに使用できる：以下の例を参照。

これらのメソッドは[`PhyloNetworks.descendencematrix`](@extref)を使用するため、`net`は前順にソートされたノードのベクターを格納するように変更される可能性がある。

# 例

```jldoctest descendence
julia> net = readnewick("(A:2.5,((B:1,#H1:0.5::0.4):1,(C:1,(D:0.5)#H1:0.5::0.6):1):0.5);");

julia> preorder!(net)

julia> using PhyloPlots

julia> plot(net, shownodenumber=true); # ノードを特定するため

julia> nodes_shifts = indexin([1,-5], [n.number for n in net.node]) # ノード1と-5で終わるエッジにシフトを置く
2-element Vector{Union{Nothing, Int64}}:
 1
 7

julia> params = ParamsBM(10, 0.1, ShiftNet(net.node[nodes_shifts], [3.0, -3.0],  net))
ParamsBM:
固定された根を持つBMのパラメータ:
mu: 10.0
Sigma2: 0.1

ネットワーク上に2つのシフトがあります:
──────────────────────────
  エッジ番号  シフト値
──────────────────────────
          8.0         -3.0
          1.0          3.0
──────────────────────────

julia> using Random; Random.seed!(2468); # 再現性のためにシードを設定

julia> sim = rand(net, params); # シフトを持つデータセットをシミュレート

julia> using DataFrames # データフレームを扱うため

julia> dat = DataFrame(trait = sim[:tips], tipnames = sim.M.tipnames);

julia> dat = DataFrame(trait = [13.391976856737717, 9.55741491696386, 7.17703734817448, 7.889062527849697],
        tipnames = ["A","B","C","D"]) # ハードコーディング、乱数生成器に依存しないように
4×2 DataFrame
 Row │ trait     tipnames 
     │ Float64   String   
─────┼────────────────────
   1 │ 13.392    A
   2 │  9.55741  B
   3 │  7.17704  C
   4 │  7.88906  D

julia> dfr_shift = descendencedataframe(net, net.node[nodes_shifts]) # シフトに一致する回帰変数
4×3 DataFrame
 Row │ shift_1  shift_8  tipnames 
     │ Float64  Float64  String   
─────┼────────────────────────────
   1 │     1.0      0.0  A
   2 │     0.0      0.0  B
   3 │     0.0      1.0  C
   4 │     0.0      0.6  D

julia> dfr = innerjoin(dat, dfr_shift, on=:tipnames); # データと回帰変数を単一のデータフレームに結合

julia> using StatsModels # 統計モデルの式のため

julia> fitBM = phylolm(@formula(trait ~ shift_1 + shift_8), dfr, net; reml=false) # 実際のフィット
PhyloNetworkLinearModel

式: trait ~ 1 + shift_1 + shift_8

モデル: ブラウン運動

パラメータ推定、MLを使用:
系統的分散率: 0.0112618

係数:
────────────────────────────────────────────────────────────────────────
                Coef.  標準誤差      t  Pr(>|t|)  下限95%  上限95%
────────────────────────────────────────────────────────────────────────
(切片)   9.48238    0.327089  28.99    0.0220    5.32632   13.6384
shift_1       3.9096     0.46862    8.34    0.0759   -2.04479    9.86399
shift_8      -2.4179     0.422825  -5.72    0.1102   -7.7904     2.95461
────────────────────────────────────────────────────────────────────────
対数尤度: 1.8937302027
AIC: 4.2125395947
```

次に、ハイブリダイゼーション後の特性のシフトを伴う超越的進化、すなわちヘテロシスを持つモデルを示します。まず、このモデルに従ってシミュレートする方法：

```jldoctest descendence
julia> nodes_hybrids = indexin([5], [n.number for n in net.node]); # ハイブリッドの下にあるエッジにシフトを置く

julia> params = ParamsBM(10, 0.1, ShiftNet(net.node[nodes_hybrids], [3.0],  net));

julia> using Random; Random.seed!(2468); # 再現性のためにシードを設定

julia> sim = rand(net, params); # シフトを持つデータセットをシミュレート

julia> dat = DataFrame(trait = sim[:tips], tipnames = sim.M.tipnames);
```

次に、超越的進化モデルの下でデータを分析する方法。以下に、再現性を高めるためにデータ値をハードコーディングします。

```jldoctest descendence
julia> dat = DataFrame(trait = [10.391976856737717, 9.55741491696386, 10.17703734817448, 12.689062527849698],
          tipnames = ["A","B","C","D"])
4×2 DataFrame
 Row │ trait     tipnames 
     │ Float64   String   
─────┼────────────────────
   1 │ 10.392    A
   2 │  9.55741  B
   3 │ 10.177    C
   4 │ 12.6891   D

julia> dfr_hybrid = descendencedataframe(net) # ハイブリッドに一致する回帰変数（すべて）
4×3 DataFrame
 Row │ shift_6  tipnames  sum     
     │ Float64  String    Float64 
─────┼────────────────────────────
   1 │     0.0  A             0.0
   2 │     0.0  B             0.0
   3 │     0.0  C             0.0
   4 │     1.0  D             1.0

julia> dfr = innerjoin(dat, dfr_hybrid, on=:tipnames); # データと回帰変数を単一のデータフレームに結合

julia> using StatsModels

julia> fitBM = phylolm(@formula(trait ~ shift_6), dfr, net; reml=false) # 実際のフィット
PhyloNetworkLinearModel

式: trait ~ 1 + shift_6

モデル: ブラウン運動

パラメータ推定、MLを使用:
系統的分散率: 0.041206

係数:
────────────────────────────────────────────────────────────────────────
                Coef.  標準誤差      t  Pr(>|t|)  下限95%  上限95%
────────────────────────────────────────────────────────────────────────
(切片)  10.064      0.277959  36.21    0.0008    8.86805   11.26
shift_6       2.72526    0.315456   8.64    0.0131    1.36796    4.08256
────────────────────────────────────────────────────────────────────────
対数尤度: -0.7006021946
AIC: 7.4012043891
```

# 参照

[`phylolm`](@ref), [`PhyloNetworks.descendencematrix`](@extref).
