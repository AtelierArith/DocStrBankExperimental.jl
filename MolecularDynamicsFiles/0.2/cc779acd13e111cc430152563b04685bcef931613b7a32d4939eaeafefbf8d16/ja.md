```julia
WriteTrajectory(
    filepath::String,
    format::MolecularDynamicsFiles.Format.T,
    exported_particle_properties::Vector{Symbol}
) -> MolecularDynamicsFiles.WriteTrajectory

```

`filepath` で指定された軌道ファイルを持つ WriteTrajectory を作成し、`format` の形式で、`exported_particle_properties` を書き込みます。

すべてのスナップショット (MDFrame オブジェクト) は、1 つのファイルに書き込むことができ、この場合、スナップショットデータはファイル内に連続して書き込まれます。

または、各フレームを別々のファイルに書き込むこともできます。`filepath` のファイル名に、マスクを表す単一のワイルドカード記号 "*" が含まれている場合です。この場合、各フレームはマスクの代わりにフレームのタイムステップを持つ別々のファイルに書き込まれます。

`filepath` のファイル名が ".gz" で終わる場合、ファイルは GZip 形式で書き込まれます。

`exported_particle_properties` には、フレームで定義されたプロパティが含まれる場合があり、また次のプロパティも含まれます: `:x`, `:y`, `:z`, `:xs`, `:ys`, `:zs`, `:xu`, `:yu`, `:zu`, `:xsu`, `:ysu`, `:zsu`, `:ix`, `:iy`, `:iz` これらはフレームデータから計算できる場合です。たとえば、フレームにアンラップされた位置がある場合、これらのプロパティはすべて計算できます。
