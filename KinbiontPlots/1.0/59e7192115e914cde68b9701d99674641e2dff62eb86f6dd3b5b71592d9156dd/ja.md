```
plot_fit_of_file(
Kinbiont_results::Any;
path_to_plot="NA", # プロットを保存するパス
display_plots=true,# Juliaでプロットを表示するかどうか
save_plots=false, # プロットを保存するかどうか
x_size=500,
pt_smoothing_derivative = 7,
y_size =750,
guidefontsize=18,
tickfontsize=16,
legendfontsize=10,
)
```

この関数は、.csvファイルからすべてのデータをプロットします。最初の列が時間であると仮定します。

# 引数:

  * `Kinbiont_results`: Kinbiontの「フィット1 .csv関数」の結果のデータ構造

# 主要引数:

  * `path_to_annotation::Any = missing`: アノテーションの.csvファイルへのパス
  * `path_to_plot= "NA"`: 文字列、プロットを保存するパス。
  * `save_plot=false` : ブール値、プロットを保存するかどうか
  * `display_plots=true`: ブール値、Juliaでプロットを表示するかどうか
  * `average_replicate=false` ブール値、レプリケートの平均を行うかどうか。アノテーションパスが提供されている場合のみ機能します
  * `x_size=300` : プロットのXサイズ、
  * `y_size=300` : プロットのYサイズ、
  * `tickfontsize = 10` : プロット内の目盛りのテキストサイズ
  * `guidefontsize = 10` : プロット内のガイドのテキストサイズ
  * `legendfontsize = 10` : プロット内の凡例のテキストサイズ

# 出力:

  * この関数の出力は、主要引数の値に応じて保存または表示されます。
