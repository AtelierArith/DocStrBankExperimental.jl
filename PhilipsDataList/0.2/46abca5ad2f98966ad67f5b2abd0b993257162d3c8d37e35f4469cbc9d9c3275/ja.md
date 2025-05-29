```
data_list_to_kspace(path_to_data_or_list; drop_dims=true,
remove_readout_oversampling=false, offset_array=false)
```

.{data/list}ファイルを読み込み、測定された「STD」サンプルをk空間に格納します。

これは、Philipsの.data/.listファイルをk空間配列に変換するための主要なエントリポイントです。データの読み取り、解析、組み立てを処理し、次元の取り扱いやオーバーサンプリングの削除に関するオプションを提供します。

## 警告

この関数は、Cartesian取得からのデータにのみ使用するべきです。非Cartesianデータに対して何が起こるかはわかりません。

## 注意

  * 各リードアウトが同じ数のサンプルを持つと仮定されています。
  * .dataおよび.listファイルは、名前が同じである必要があります（拡張子を除く）。この関数は、パスに拡張子がなくても問題ありません。なぜなら、この関数はそれぞれのファイルを読み込むために.pathに.dataと.listを追加するからです。
  * k空間には名前付き次元があります（`NamedDimsArray`です）。これにより、例えば、インデックス`i`のチャネルからすべてのサンプルを取得することができます。`kspace[chan=i]`で。
  * 次元の順序は`DIMENSIONS_STD`定数と同じです。ただし、`drop_dims=true`の場合、サイズ1の次元は削除されます。
  * `offsetarray`が`true`の場合、k空間はOffsetArrayとして格納され、リストファイルに含まれる範囲をインデックスとして使用できます。例えば、`kspace[kx=0, ky=0, kz=0, ...]`はk空間の中心のk空間値を返します。
  * `remove_readout_oversampling`が`true`の場合、リードアウトオーバーサンプリングはk空間をクロップし、リードアウト方向に沿ってifftを適用することによって削除されます。
