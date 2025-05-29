```
distributed_cic_map(cic_filename::String, Nsubfiles::Integer,
                    mapping_function::Function,
                    Nimages::Integer, param::mappingParameters;
                    reduce_image::Bool=true,
                    Ndim::Integer=2,
                    snap::Integer=0,
                    units::String="",
                    vtk::Bool=true)
```

サブファイルごとに1つのcicマップを計算するためにワーカーを動的にディスパッチし、結果を合計してfitsファイルに保存します。

# 引数

  * `cic_filename::String`: 画像を保存するファイルの名前
  * `Nsubfiles::Integer`: スナップショットが分散されるサブファイルの数。
  * `mapping_function::Function`: サブファイルごとに実行される関数。cic画像とweight_imageの`Tuple`を返す必要があります。
  * `Nimages::Integer=1`: 同時に構築されるcic画像の数。複数の量を一度にマッピングする場合にのみ有用で、デフォルトは`1`です。
  * `param::mappingParameters`: 画像を通常の方法で保存するために必要なマッピングのパラメータ。
  * `reduce_image`: 最終画像がweight画像で割られるべきかどうか、`true`に設定します。
  * `Ndim::Integer=2`: 画像の次元、`2`または`3`のいずれかでなければなりません。
  * `snap::Integer=0`: 入力スナップショットの番号、画像を保存するために使用されます。
  * `units::String=""`: 画像の単位、画像を保存するために使用されます。
