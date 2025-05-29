```
get_genotypes(file::Union{AbstractString,Array{Float64,2},Array{Float32,2},Array{Any,2},DataFrames.DataFrame},G=false;
              separator=',',header=true,rowID=false,
              center=true,quality_control=false,
              method = "RR-BLUP",Pi = 0.0,estimatePi = true,estimateScale=false,
              G_is_marker_variance = false,df = 4.0)
```

  * ジェノタイプファイル/マトリックスからマーカー情報を取得します。このファイルはマーカーポジションで列方向にソートされている必要があります。

      * テキストファイルが提供される場合、ファイル形式は次のようになります：

        ```
        Animal,marker1,marker2,marker3,marker4,marker5
        S1,1,0,1,1,1
        D1,2,0,2,2,1
        O1,1,2,0,1,0
        O3,0,0,2,1,1
        ```
      * nxpのジェノタイプマトリックス（ArrayまたはDataFrame）が提供される場合、ここでnは個体の数、pはマーカーの数です。

          * このマトリックスはマーカーポジションで列方向にソートされている必要があります。
          * rowIDは個体IDのベクターで、例えばrowID=["a1","b2","c1"]; 省略した場合、IDは1:nに設定されます。
          * headerは["id"; "mrk1"; "mrk2";...;"mrkp"]のようなヘッダーベクターです。省略した場合、マーカー名は1:pに設定されます。
  * `quality_control`=trueの場合、デフォルトは`true`です。

      * 欠損したジェノタイプは`9`で示され、列の平均で置き換えられます。ユーザーは分析の前に欠損したジェノタイプを補完することもできます。
      * マイナーアレル頻度`MAF`の閾値はデフォルトで`0.01`が使用され、固定ロキは削除されます。
  * **G**は自由度**df**のために割り当てられたゲノム分散の平均で、デフォルトは4.0です。**G**が提供されない場合、応答（表現型）から値が計算されます。
  * 利用可能な`methods`には「従来型（マーカーなし）」、「RR-BLUP」、「BayesA」、「BayesB」、「BayesC」、「ベイジアンラッソ」、および「GBLUP」が含まれます。
  * ベイジアン変数選択法では、単一特性分析のための`Pi`は数値であり、多重特性分析のための`Pi`は`Pi=Dict([1.0; 1.0]=>0.7,[1.0; 0.0]=>0.1,[0.0; 1.0]=>0.1,[0.0; 0.0]=>0.1)`のような辞書です。単一特性分析では「すべてのマーカーが効果を持つ（Pi = 0.0）」がデフォルトであり、多重特性分析では「すべてのマーカーがすべての特性に効果を持つ（Pi=Dict([1.0; 1.0]=>1.0,[0.0; 0.0]=>0.0))」がデフォルトです。`Pi`は`estimatePi` = trueの場合に推定され、デフォルトは`false`です。
  * マーカー効果分散の事前のスケールパラメータは、`estimateScale` = trueの場合に推定され、デフォルトは`false`です。
