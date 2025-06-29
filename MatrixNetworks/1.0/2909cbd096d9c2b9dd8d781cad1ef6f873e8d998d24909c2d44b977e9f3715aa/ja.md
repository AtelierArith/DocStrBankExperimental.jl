# 'generalized*preferential*attachment_graph'

Avin, Lotker, Nahum, Peleg の説明に従った一般化された優先的接続グラフのインスタンスを生成します。これは次のように生成される無向グラフです：

  * k0ノードのクリークから始める
  * n - k0 頂点を追加し、各時間ステップで次の3つのイベントのいずれかが発生します：新しい

ノードが確率 p で追加され、既存の2つのノードの間に新しいエッジが確率 r で追加され、2つの新しいノードがそれらの間にエッジを持って追加される確率は 1 - p - r です。

## 関数

以下の関数は同義語です

  * 'generalized*preferential*attachment_graph'
  * 'gpa_graph'

および

  * 'generalized*preferential*attachment_edges!'
  * 'gpa_edges!'

計算関数は次のとおりです

  * 'gpa_graph(n,p,r,k0)' k0クリークとn個のノードを持つGPAグラフを生成します。これはMatrixNetwork型を返します。
  * 'gpa_graph(n,p,r,k0,Val{true})' k0クリークとn個のノードを持つGPAグラフを生成し、自己ループを許可します。これはMatrixNetwork型を返します。

エッジ関数は次のとおりです

  * 'gpa_edges!(n,p,r,edges,n0)' 既存のセットに新しいエッジを追加し、n0時間ステップを取ります。エッジは次の3つの方法のいずれかで追加されます：新しいノードから既存のノードへの確率 p、既存の2つのノードの間に確率 r、新しい2つのノードの間に確率 1-p-r
  * 'gpa_edges!(n,p,r,edges,n0,Val{true})' 既存のセットに新しいエッジを追加し、n0時間ステップを取ります。エッジは次の3つの方法のいずれかで追加されます：新しいノードから既存のノードへの確率 p、既存の2つのノードの間に確率 r（自己ループを許可）、新しい2つのノードの間に確率 1-p-r

## 入力

  * 'n': 最終グラフのノード数。
  * 'p': ノードイベントの確率、pは定数でなければなりません。
  * 'r': エッジイベントの確率、rは定数でなければなりません。p+r <=1
  * 'k0': 開始クリークのノード数。
  * 'Val{true}': 自己ループが許可される場合はこのパラメータを含めます。デフォルトはfalseです。
  * 'edges': 新しいエッジを生成する過程で操作されるエッジのリスト。

## 出力

  * 一般化された優先的接続グラフのためのマトリックスネットワーク型。
  * 'edges': 更新されたエッジのリスト。

例: generalized*preferential*attachment_graph(100,1/3,1/2,2)
