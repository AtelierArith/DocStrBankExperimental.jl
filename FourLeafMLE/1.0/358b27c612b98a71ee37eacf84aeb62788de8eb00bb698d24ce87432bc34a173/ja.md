```
make_averaged_classification_plot(sequence_length,
                                  x_values, y_values, scores;
                                  topology=nothing,
                                  marker_size=nothing,
                                  Hadamard_mode=false)
```

# 説明

`generate_averaged_classification_plot_data` からのデータを使用して、指定されたトポロジーと一致するMLEを持つサンプルの割合を表す点を持つフェルゼンシュタインプロットを作成します。

# 出力

`plots/` ディレクトリにプロットを保存します。
