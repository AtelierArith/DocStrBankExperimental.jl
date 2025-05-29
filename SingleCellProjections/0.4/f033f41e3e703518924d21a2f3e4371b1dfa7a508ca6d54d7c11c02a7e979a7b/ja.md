```
update_matrix(data::DataMatrix, matrix, model=nothing;
              var::Union{Symbol,String,DataFrame} = "",
              obs::Union{Symbol,String,DataFrame} = "")
```

新しい値で `data` の一部を置き換えることによって新しい `DataMatrix` を作成します。主に新しい `ProjectionModel` を実装する際に便利です。

  * `matrix` - 新しい行列。
  * `model` - `data` のモデルのリストに追加されます。`nothing` に設定すると、結果の `models` のリストは空になります。

キーワード引数:

  * `var` - 次のいずれか:

      * `:copy` - `data` からコピーします。
      * `:keep` - `data` と `var` を共有します。
      * `::DataFrame` - 変数の注釈を持つ新しいテーブルで置き換えます。
      * `prefix::String` - プレフィックス、新しい変数は prefix1, prefix2 などと名付けられます。
  * `obs` - `var` を参照してください。
