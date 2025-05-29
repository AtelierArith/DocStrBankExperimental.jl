```
TimeSeriesCallback(semi, point_coordinates;
                   interval=1, solution_variables=cons2cons,
                   output_directory="out", filename="time_series.h5",
                   RealT=real(solver), uEltype=eltype(cache.elements))
```

`point_coordinates`で指定された点ごとのデータを`interval`時間ステップごとに記録するコールバックを作成します。点の座標は、座標タプルのベクトルまたは、最初の次元が点番号、第二の次元が座標次元の二次元配列として指定できます。デフォルトでは、保守的変数が記録されますが、異なる変換関数を`solution_variables`に渡すことで制御できます。

最後の時間ステップの後、結果は`output_directory`内のHDF5ファイル`filename`に保存されます。

実データ型`RealT`と解変数のデータ型`uEltype`は、それぞれソルバーとキャッシュで使用される型にデフォルト設定されています。

現在、このコールバックは[`TreeMesh`](@ref)および[`UnstructuredMesh2D`](@ref)にのみ実装されています。
