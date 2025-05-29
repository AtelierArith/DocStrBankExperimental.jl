```
add_genotypes(mme::MME,M::Union{AbstractString,Array{Float64,2},Array{Float32,2},Array{Any,2},DataFrames.DataFrame},G=false;
              header=false,rowID=false,separator=',',
              center=true,G_is_marker_variance=false,df=4)
```

  * ジェノタイプファイルまたはジェノタイプのnxp行列M（ArrayまたはDataFrame）からマーカー情報を取得します。ここで、nは個体の数、pはマーカーの数です。このファイル/行列は、マーカーポジションで列方向にソートされている必要があります。
  * **G**は、自由度**df**の下で遺伝的分散のために割り当てられた事前の平均で、デフォルトは4.0です。**G**が提供されていない場合、応答（表現型）から値が計算されます。
  * テキストファイルが提供される場合、ファイル形式は次のようになります：

      * ```
        Animal,marker1,marker2,marker3,marker4,marker5
        S1,1,0,1,1,1
        D1,2,0,2,2,1
        O1,1,2,0,1,0
        O3,0,0,2,1,1
        ```
  * nxp行列のジェノタイプ（ArrayまたはDataFrame）が提供される場合、ここでnは個体の数、pはマーカーの数です。

      * この行列は、マーカーポジションで列方向にソートされている必要があります。
      * rowIDは個体IDのベクターで、例としてrowID=["a1","b2","c1"]; 省略した場合、IDは1:nに設定されます。
      * headerは["id"; "mrk1"; "mrk2";...;"mrkp"]のようなヘッダーのベクターです。省略した場合、マーカー名は1:pに設定されます。
