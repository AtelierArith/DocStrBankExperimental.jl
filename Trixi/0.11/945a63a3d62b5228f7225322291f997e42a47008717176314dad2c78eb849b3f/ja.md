```
StructuredMesh(cells_per_dimension, mapping;
               RealT = Float64,
               periodicity = true,
               unsaved_changes = true, 
               mapping_as_string = mapping2string(mapping, length(cells_per_dimension), RealT=RealT))
```

指定されたサイズと形状の `StructuredMesh` を作成し、`RealT` を座標タイプとして使用します。

# 引数

  * `cells_per_dimension::NTupleE{NDIMS, Int}`: 各次元のセルの数。
  * `mapping`: 参照メッシュを物理ドメインに変換する `NDIMS` 変数の関数。            `mapping_as_string` が定義されていない場合、この関数は再起動を可能にするために            `mapping` という名前で定義されている必要があります。            これは将来的に変更される予定です。詳細は [https://github.com/trixi-framework/Trixi.jl/issues/541](https://github.com/trixi-framework/Trixi.jl/issues/541) を参照してください。
  * `RealT::Type`: 座標に使用するタイプ。
  * `periodicity`: すべての境界が周期的であるかどうかを決定する `Bool` か、                各次元の境界がこの次元で周期的であるかどうかを決定する `NTuple{NDIMS, Bool}`。
  * `unsaved_changes::Bool`: `true` に設定すると、メッシュはメッシュファイルに保存されます。
  * `mapping_as_string::String`: `mapping` を定義するコード。                              `CodeTracking` が関数定義を見つけられない場合、ここに直接渡すことができます。                              コード文字列は `mapping` という名前のマッピング関数を定義する必要があります。                              これは将来的に変更される予定です。詳細は [https://github.com/trixi-framework/Trixi.jl/issues/541](https://github.com/trixi-framework/Trixi.jl/issues/541) を参照してください。
