```
System(coordinate_file, force_field; <keyword arguments>)
```

Chemfilesで読み取れるファイル形式の座標ファイルを読み込み、それに力場を適用します。

原子名は残基テンプレートと正確に一致する必要があります - 残基テンプレートの検索は行われません。

```
System(coordinate_file, topology_file; <keyword arguments>)
System(T, coordinate_file, topology_file; <keyword arguments>)
```

Gromacsの座標ファイルと、すべてのインクルードが1つのファイルにまとめられたGromacsのトポロジーファイルを読み込みます。

Gromacsファイルの読み込みは実験的と見なされるべきです。Gromacsファイルを読み込む際には、`implicit_solvent`、`kappa`、および`rename_terminal_res`キーワード引数は使用できません。

# 引数

  * `boundary=nothing`: シミュレーションに使用される境界ボックスで、デフォルトではファイルから読み取られます。
  * `velocities=nothing`: システム内の原子の速度で、デフォルトではゼロに設定されます。
  * `loggers=()`: シミュレーション中に関心のある特性を記録するロガー。
  * `units::Bool=true`: Unitful量を使用するかどうか。
  * `array_type=Array`: シミュレーションの配列タイプで、例えばGPUサポートのために`CuArray`や`ROCArray`を使用します。
  * `dist_cutoff=1.0u"nm"`: 長距離相互作用のためのカットオフ距離。
  * `dist_neighbors=1.2u"nm"`: 隣接リストのためのカットオフ距離で、`dist_cutoff`より小さくしてはいけません。[`GPUNeighborFinder`](@ref)が使用される場合は関係ありません。なぜなら、隣接は各ステップで計算されるからです。
  * `center_coords::Bool=true`: シミュレーションボックス内の座標を中心にするかどうか。
  * `neighbor_finder_type`: 使用する隣接探索器、デフォルトはCPU上の[`CellListMapNeighborFinder`](@ref)、CUDA互換GPU上の[`GPUNeighborFinder`](@ref)、および非CUDA互換GPU上の[`DistanceNeighborFinder`](@ref)です。
  * `data=nothing`: システムに関連付けられた任意のデータ。
  * `implicit_solvent=nothing`: 文字列を指定して暗黙の溶媒モデルを追加します。オプションは"obc1"、"obc2"、および"gbn2"です。
  * `kappa=0.0u"nm^-1"`: 使用される場合の暗黙の溶媒モデルのためのカッパ値。
  * `rename_terminal_res=true`: 最初と最後の残基の名前を適切な原子テンプレートに一致させるために変更するかどうか。例えば、最初の（N末端）残基は"MET"から"NMET"に変更される可能性があります。
