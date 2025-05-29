```
io = csopen(containers[, mode="r"]; axis_lengths::Vector{Int}[, optional keyword arguments])
```

はCloudSeisデータセットへのハンドルを返し、`container::Container`はすべての範囲が単一のコンテナにあるデータセットに対応し、`container::Vector{<:Container}`は範囲が複数のコンテナに分割されているデータセットに対応します。コンテナは、POSIXフォルダー（container::Folder）またはクラウドストレージコンテナ（例：container::AzContainer）である可能性があります。

`mode`は、`"r"` - 読み取り、`"w"` - 書き込み、`"r+"` - 既存のデータセットを読み書きのために開くのいずれかです。

`mode="w"`の場合、`axis_lengths`は必須のキーワード引数です。`axis_lengths`はコンテナのサイズを指定します。`axis_lengths`ベクターは、少なくとも長さ3である必要があります。

# オプションのキーワード引数

  * `similarto::String` 既存のCloudSeisデータセット。設定されている場合、他のすべての名前付き引数は、既存のCloudSeisデータセットに属するデータコンテキストを変更するために使用できます。
  * `history` 履歴辞書（下記のノートを参照して、どのようにフォーマット/構築するかを確認してください）。
  * `datatype::String` 例としては`CMP`、`SHOT`などがあります。設定されていない場合、`UNKNOWN`が使用されます。
  * `traceformat::DataType=Float32` サポートされていません。`traceformat=Float32`に対してのみテストしています。
  * `byteorder::String`
  * `extents::Vector{UnitRange}` 各範囲の整数範囲（フレーム範囲）のリスト。各範囲はブロックストレージ内のオブジェクトにマッピングされます（`extents`、`frames_per_extent`、`mbytes_per_extent`のいずれか1つのみ設定してください）。
  * `frames_per_extent::Int` 各範囲の名目上のフレーム数（`extents`、`frames_per_extent`、`mbytes_per_extent`のいずれか1つのみ設定してください）。
  * `mbytes_per_extent::Int` 各範囲の名目上のサイズ（メガバイト単位）（`extents`、`frames_per_extent`、`mbytes_per_extent`のいずれか1つのみ設定してください）。
  * `geometry::Geometry` CloudSeisファイルに埋め込むことができるオプションの三点ジオメトリ。
  * `tracepropertydefs::Vector{TracePropertyDef}` トレースプロパティ定義の配列。これらは軸プロパティ定義に加えて存在します。
  * `dataproperties::Vector{DataProperty}` データプロパティの配列。データセットごとに1つのプロパティがあり、トレースごとに1つのプロパティ（`tracepropertydefs`に対しては真です）。
  * `axis_propdefs::Vector{TracePropertyDef}` CloudSeis軸に対応するトレースプロパティ。設定されていない場合、`SAMPLE`、`TRACE`、`FRAME`、`VOLUME`、`HYPRCUBE`が使用されます。
  * `axis_units::Vector{String}` CloudSeis軸に対応する単位。例：`SECONDS`、`METERS`など。設定されていない場合、`UNKNOWN`が使用されます。
  * `axis_domains::Vector{String}` CloudSeis軸に対応するドメイン。例：`SPACE`、`TIME`など。設定されていない場合、`UNKNOWN`が使用されます。
  * `axis_pstarts::Vector{Float64}` 各軸の物理的起点。設定されていない場合、各軸の物理的起点には`0.0`が使用されます。
  * `axis_pincs::Vector{Float64}` 各軸の物理的デルタ。設定されていない場合、各軸の物理的デルタには`1.0`が使用されます。
  * `axis_lstarts::Vector{Int}` 各軸の論理的開始。設定されていない場合、各軸の論理的開始には`1`が使用されます。
  * `axis_lincs::Vector{Int}` 各軸の論理的インクリメント。設定されていない場合、各軸の論理的インクリメントには`1`が使用されます。
  * `compressor="leftjustify"` ディスクに書き込む前にキャッシュを圧縮します。これは、可変フォールドのデータに特に便利です。選択肢は次のとおりです: ("none", "blosc", "leftjustify", "zfp", "cvx")
  * `compressor_options=()` 圧縮アルゴリズムにキーワード引数としてオプションを渡します。現在、`"zfp"`と`"cvx"`のみがオプションを持っています[1]

# 例

## Azureストレージ

```julia
using AzStorage, CloudSeis
container = AzContainer("mydataset-cs"; storageaccount="mystorageaccount")
io = csopen(container, "w"; axis_lengths=[10,11,12], axis_pincs=[0.004,10.0,20.0])
close(io)
```

## POSIXストレージ

```
using AzStorage, FolderStorage
container = Folder("mydataset-cs")
io = csopen(container, "w"; axis_lengths=[10,11,12], axis_pincs=[0.004,10.0,20.0])
```

# ノート

  * `similarto`オプションを使用する場合、`axis_lengths`を介してデータセットの次元数を変更できます。次元数を縮小すると、

さまざまなデータセットプロパティ（例：`axis_units`）が切り捨てられます。切り捨ては、適切なキーワード引数を使用してカスタマイズできます。

  * zfp圧縮オプションは`tol`、`precision`、`rate`です。例えば：

```
using AzStorage, CloudSeis
container = AzContainer("mydataset-cs"; storageaccount="mystorageacccount")
io = csopen(container, "w"; axis_lengths=[10,11,12], compressor="zfp", compressor_options=(tol=1e-4,))
```

詳細についてはZFPCompressor.jlを参照してください。`compressor_options`が指定されていない場合、デフォルトは`(precision=16,)`です。また、`compressor_options=()`はZFPのロスレス圧縮をもたらします。ZFPのロスレス圧縮は、`compressor_options`の選択に関係なく、ヘッダーとフォールドマップに使用されます。

  * cvx圧縮オプションは`b1`、`b2`、`b3`、`scale`です。例えば：

```

```

詳細についてはCvxCompress.jlを参照してください。`compressor_options`が指定されていない場合、デフォルトは`(b1=16,b2=16,b3=16,scale=1e-2)`です。

  * 履歴辞書は特定の構造に従う必要があります。既存のデータセットから履歴を取得するには`history(io::CSeis)`を使用し、履歴を構築および/または拡張するには`history!`を使用できます。一般的な構造は次のとおりです。

```julia
Dict(
    "inputs" => [
        Dict(
            "container" => container, # 入力データセットの場所を説明する辞書。
            "history" => 履歴辞書で、再帰的に入力データセットの履歴を埋め込みます。
        )
    ],
    "flow" => Dict(
        "flow" => Dict(
            "parameters" => flowparameters, # すべてのプロセスに適用されるパラメータを説明する辞書
            "processes" => [
                "process" => process, # 実行されたプロセスを一意に特定する辞書または文字列
                "parameters" => parameters # プロセスに渡されるパラメータを説明する辞書
            ]
        )
    )
)
```
