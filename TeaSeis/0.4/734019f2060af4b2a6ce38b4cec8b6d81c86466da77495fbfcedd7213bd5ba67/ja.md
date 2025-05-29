```
jsopen(filename, mode, [parameters])
```

新しいまたは既存のJavaSeisデータセットを`filename::String`という名前で、`mode::String`で開きます。`mode`は、`"r"`（読み取り）、`"w"`（書き込み/作成）、または`"r+"`（読み取りと書き込み）のいずれかである必要があります。ファイル名には「.js」拡張子を付けるのが慣例です。

`mode`の値に`"w"`が使用される場合、`axis_lengths`という名前のパラメータが必要であり、いくつかのオプションの名前付き関数パラメータが利用可能です。

# parameters

  * `similarto::String` 既存のJavaSeisデータセット。設定されている場合、他のすべての名前付き引数は、既存のJavaSeisデータセットに属するデータコンテキストを変更するために使用できます。
  * `description::String` データセットの説明。設定されていない場合、ファイル名から説明が解析されます。
  * `mapped::Bool` データセットが完全（欠損フレーム/トレースなし）の場合、これを`false`に設定する方が効率的な場合があります。デフォルトは`true`です。
  * `datatype::String` 例としては`CMP`、`SHOT`などがあります。設定されていない場合、`UNKNOWN`が使用されます。
  * `dataformat::Type` `Float32`および`Int16`から選択します。設定されていない場合、`Float32`が使用されます。
  * `dataorder::String`（サポートされていません）
  * `axis_lengths::Array{Int}` JavaSeisデータコンテキストの各次元（サンプル/トレース/フレーム/ボリューム/ハイパーキューブ）のサイズ
  * `axis_propdefs::Array{TracePropertyDef}` JavaSeis軸に対応するトレースプロパティ。設定されていない場合、`SAMPLE`、`TRACE`、`FRAME`、`VOLUME`および`HYPRCUBE`が使用されます。
  * `axis_units::Array{String}` JavaSeis軸に対応する単位。例：`SECONDS`、`METERS`など。設定されていない場合、`UNKNOWN`が使用されます。
  * `axis_domains::Array{String}` JavaSeis軸に対応するドメイン。例：`SPACE`、`TIME`など。設定されていない場合、`UNKNOWN`が使用されます。
  * `axis_lstarts::Array{Int}` 各軸の論理原点。設定されていない場合、各軸の論理原点には`1`が使用されます。
  * `axis_lincs::Array{Int}` 各軸の論理増分。設定されていない場合、各軸の論理増分には`1`が使用されます。
  * `axis_pstarts::Array{Float64}` 各軸の物理原点。設定されていない場合、各軸の物理原点には`0.0`が使用されます。
  * `axis_pincs::Array{Float64}` 各軸の物理増分。設定されていない場合、各軸の物理増分には`1.0`が使用されます。
  * `data_properties::Array{DataProperty}` カスタムトレースプロパティの配列。これらは`SSPROPS.md`にリストされているプロパティに加えて追加されます。
  * `properties::Array{TracePropertyDef}` カスタムデータプロパティの配列。上記の`properties`のように、トレースごとではなく、データセットごとに1つのプロパティです。
  * `geometry::Geometry` JavaSeisファイルに埋め込むことができるオプションの三点ジオメトリ。
  * `secondaries::Array{String}` ファイルの範囲を保存するために使用されるファイルシステムの場所の配列。設定されていない場合、*プライマリ*ストレージが使用されます。
  * `nextents::Int64` データを保存するために使用されるファイル範囲の数。設定されていない場合、ヒューリスティックが使用されて範囲の数が選択されます。ヒューリスティックは：min(256,10 + (FRAMEWORK_SIZE)/(2*1024^3))です。
  * `properties_add::Array{TracePropertyDef}` `similarto`が指定されている場合、これを使用して`similarto`ファイルに既に存在するトレースプロパティに追加します。
  * `properties_rm::Array{TracePropertyDef}` `similarto`が指定されている場合、これを使用して`similarto`ファイルに既に存在するトレースプロパティを削除します。
  * `dataproperties_add::Array{DataProperty}` `similarto`が指定されている場合、これを使用して`similarto`ファイルに既に存在するデータセットプロパティに追加します。
  * `dataproperties_rm::Array{DataProperty}` `similarto`が指定されている場合、これを使用して`similarto`ファイルに既に存在するデータセットプロパティを削除します。
