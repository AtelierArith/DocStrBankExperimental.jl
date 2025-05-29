```
plot_data(
label_exp::String, 
path_to_data::String; 
path_to_annotation::Any = missing,
path_to_plot="NA",
display_plots=true,
save_plots=false,
overlay_plots=true, 
do_blank_subtraction="NO", vg)
avg_replicate=false, 
correct_negative="thr_correction", 
thr_negative=0.01 ,
blank_value = 0.0,
blank_array = [0.0],
text_size = 10,
x_size =
y_size =
)
```

この関数は、.csvファイルからすべてのデータをプロットします。最初の列が時間であると仮定します。

# 引数:

  * `label_exp::String`: 実験のラベル。
  * `path_to_data::String`: データの.csvへのパス。

# 主要引数:

  * `path_to_annotation::Any = missing`: アノテーションの.csvへのパス。
  * `path_to_plot= "NA"`: 文字列、プロットを保存するパス。
  * `save_plot=false` : ブール値、プロットを保存するかどうか。
  * `display_plots=true`: ブール値、Juliaでプロットを表示するかどうか。
  * `overlay_plots =true` : ブール値、trueの場合、すべてのデータセット曲線を重ねた1つのプロットを作成します。
  * `blank_subtraction="NO"`: 文字列、ブランクの引き算をどのように行うか、オプションは「NO」、「avg*subtraction」（ブランクの平均値の引き算）および「time*avg」（ブランクの時間平均値の引き算）。
  * `average_replicate=false` ブール値、レプリケートの平均を行うかどうか。アノテーションパスが提供されている場合のみ機能します。
  * `blank_value = 0.0`: `path_to_annotation = missing`かつ`blank_subtraction != "NO "`の場合にのみ使用されます。ブランクの平均値として使用されます。
  * `blank_array = [0.0]`: `path_to_annotation = missing`かつ`blank_subtraction != "NO "`の場合にのみ使用されます。ブランク値の配列として使用されます。
  * `correct_negative="thr_correction"`  : 文字列、ブランク引き算後の負の値をどのように扱うか。「thr*correction」の場合、ブランクを引いたデータの最小値にスレッショルドを設定し、「blank*correction」の場合、ブランク分布を使用して負の値を補完し、「remove」の場合、値は単に削除されます。
  * `x_size=300` : プロットのXサイズ、
  * `y_size=300` : プロットのYサイズ、
  * `text_size = 10` : プロット内のテキストのサイズ。

# 出力:

  * この関数の出力は、主要引数の値に応じて保存または表示されます。
