`convertdim(x::NDSparse, d::DimName, xlate; agg::Function, vecagg::Function, name)`

指定された次元の各インデックスに関数または辞書 `xlate` を適用します。マッピングが多対一の場合、結果を集約するために `agg` または `vecagg` が使用されます。`agg` が渡された場合、データに対して2引数の還元関数として使用されます。`vecagg` が渡された場合、データを集約するためのベクトルからスカラーへの関数として使用されます。`name` はオプションで、変換された次元の新しい名前を指定します。
