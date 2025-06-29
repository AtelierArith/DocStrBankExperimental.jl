```julia
ReadTrajectory(
    filepath::String,
    format::MolecularDynamicsFiles.Format.T
) -> MolecularDynamicsFiles.ReadTrajectory

```

`filepath`で指定された軌道ファイルを、`format`の形式でReadTrajectoryを作成します。

ファイルは、gzipで圧縮されている可能性のあるプレーンテキストファイルです。

軌道は、スナップショットが1つずつ追加された単一のファイルに含まれる場合があります。これは、LAMMPS DumpおよびXYZ形式でのみ可能です。

あるいは、軌道はディレクトリ内のファイルのセットとして定義される場合があり、各ファイルには単一のスナップショット（MDFrame）のデータが含まれています。この場合、ファイルはファイルパスで指定され、ファイル名にはマスクシンボル'*'が含まれます。マスクシンボルを含むファイル名は、そのディレクトリ内のすべてのファイルパスと一致し、マスクシンボルの代わりに整数が入ります。フレームのタイムステップは、ファイル自体にタイムステップが指定されていない場合、マスクからも読み取られます。

# 引数:

  * `filepath`: 軌道ファイルへのパス。ディスク上のファイルへのパス、またはマスクを表す単一のワイルドカード"*"を含むファイル名のパスのいずれかです。マスクを含むファイル名は、マスクの代わりに整数（タイムステップ）が入るすべてのファイルパスと一致します。
  * `format`: 軌道のファイル形式（例えば、Format.LAMMPSDump）
