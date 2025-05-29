```
make_classification_plot(sequence_length,
                         x_values, y_values,
                         categorical_data;
                         marker_size=nothing,
                         Hadamard_mode=false)
```

# 説明

関数 `generate_classification_plot_data` から得られたデータを使用してプロットを作成します。

# 引数

  * `sequence_length` : 各パラメータレジーム（すなわち、プロット上の各点）に対して生成されるデータのサイズ（塩基対単位）。
  * `x_values`, `y_values`, `categorical_data` : `generate_classification_plot_data` の出力。
  * `marker_size` : オプションのパラメータ。散布図によって作成される正方形のサイズを決定します。ステップサイズ（これは自動的にベクトル `x_values` と `y_values` から推測されます）に応じて、調整が必要な場合があります。理想的には、`marker_size` は正方形が見えるように十分大きく、ほぼまたは正確に隣接するべきですが、重ならないほどの大きさであるべきです。ユーザーが値を提供しない場合、適切なデフォルトが選択され、これは `171` を `max(number_of_x_values,number_of_y_values)` で割った値になります。
  * `Hadamard_mode` : オプションのパラメータ。プロットモードを指定します。true の場合、`x_values` と `y_values` は Hadamard エッジパラメータとして解釈されます。false の場合、これらはサイトあたりの期待される変異数で測定された枝長距離として解釈されます。これはプロットの軸とラベルに影響します。見栄えの良いプロットを得るためには、この変数の値はデータ生成時に使用した値と同じであるべきです（そうでないとボックスが均等に配置されません）。

# 出力

要約に示されているようなプロット。プロットは "plots/hadamard-plot.svg" に .svg ファイルとして保存されます。

# 例

要約にある図を再現するには、次のように実行します。

```
    sequence_length=1000
    x_values, y_values, categorical_results = generate_classification_plot_data(sequence_length, .01, .01, .99, .99, 300, 300, Hadamard_mode=true)
    make_classification_plot(sequence_length, x_values, y_values, categorical_results, Hadamard_mode=true);
```

これにより、プロットの .svg 画像が作業ディレクトリに保存されます。
