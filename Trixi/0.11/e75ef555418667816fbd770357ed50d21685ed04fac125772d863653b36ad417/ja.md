```
VisualizationCallback(; interval=0,
                        solution_variables=cons2prim,
                        variable_names=[],
                        show_mesh=false,
                        plot_data_creator=PlotData2D,
                        plot_creator=show_plot,
                        plot_arguments...)
```

シミュレーション中に結果を視覚化するコールバックを作成します。これは*インシチュ視覚化*としても知られています。

!!! warning "実験的な実装"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。


`interval`は、新しいプロットが生成されるまでの時間ステップの反復回数を指定します。プロット可能な変数は、[`SaveSolutionCallback`](@ref)と同様に`solution_variables`パラメータで設定されます。実際にプロットされる変数は、`variable_names`に単一の文字列または文字列のリストを提供することで選択できます。また、`show_mesh`が`true`の場合、メッシュを含む追加のプロットが生成されます。

生成される図をカスタマイズするために、`plot_data_creator`を使用して異なるプロットデータタイプを利用できます。`plot_creator`を使用すると、結果を視覚化するための独自の関数をさらに指定でき、これはデフォルトの実装[`show_plot`](@ref)と同じインターフェースをサポートする必要があります。残りのキーワード引数はすべて収集され、プロットコマンドへの追加引数として渡されます。
