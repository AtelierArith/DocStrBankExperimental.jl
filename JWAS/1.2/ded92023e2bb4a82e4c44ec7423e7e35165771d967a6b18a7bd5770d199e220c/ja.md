```
GWAS(model,map_file,marker_effects_file...;
     window_size = "1 Mb",sliding_window = false,
     GWAS = true, threshold = 0.001,
     genetic_correlation = false,
     header = true)
```

ゲノムウィンドウベースのGWASを実行します。

  * マーカー効果のMCMCサンプルは、区切り文字が','の**marker*effects*file**に保存されます。
  * **model**は、分析に使用されるmodel::MMEまたは遺伝子型共変量行列M::Arrayです。
  * **map_file**には、区切り文字が','の（ソートされた）マーカー位置情報が含まれています。マップファイルが提供されない場合、すなわち**map_file**=`false`の場合、各1 Mbウィンドウに**window_size**マーカーを持つ偽のマップファイルが生成され、各1 Mbウィンドウがテストされます。
  * 2つの**marker*effects*file**が提供され、**genetic_correlation** = trueの場合、各ウィンドウのゲノム相関が計算されます。
  * 統計は、デフォルトでサイズ*window_size*の非重複ウィンドウに対して計算されます。**sliding_window** = trueの場合、重複するスライディングウィンドウの統計が計算されます。
  * マップファイルのフォーマット：

```
markerID,chromosome,position
m1,1,16977
m2,1,434311
m3,1,1025513
m4,2,70350
m5,2,101135
```
