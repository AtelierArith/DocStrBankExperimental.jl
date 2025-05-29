```
FAUST(split=:train; dir=nothing)
```

MPI FAUSTデータセット（2014年）。

FAUSTには、10人の異なる被験者の30種類のポーズでの300件の実際の高解像度人間スキャンが含まれており、自動的に計算されたグラウンドトゥルスの対応が付いています。

各スキャンは、3Dマルチステレオシステムを使用して取得された高解像度の三角形メッシュで、非水密です。

FAUSTは、トレーニングセットとテストセットに分かれています。トレーニングセットには、対応するグラウンドトゥルスのアライメントを持つ100件のスキャン（被験者ごとに10件）が含まれています。テストセットには200件のスキャンが含まれています。FAUSTベンチマークは、60件が被験者内マッチングを必要とし、40件が被験者間マッチングを必要とする2つのクラスに分けられた100件の事前選択されたスキャンペアを定義しています。

データセットは、[ウェブサイト](http://faust.is.tue.mpg.de/)から手動でダウンロードし、正しい場所に抽出する必要があります。データセットを配置する場所については、例のセクションを参照してください。

# データセット変数

  * `scans`: `Mesh`の形式の非水密スキャンのベクター。
  * `registrations`: `scans`の各スキャンに対応する登録のベクター。`registrations`も`scans`と同様に`Mesh`の形式です。
  * `labels`: トレーニングセットの各スキャンに対して、対応するスキャンの頂点数と同じ長さのブールベクターを提供します。これは、対応する登録によって信頼性のある登録が行われた頂点を表します。
  * `metadata`: データセットに関する追加情報を含む辞書。現在、`:test`スプリットのみが、著者によって提案されたインターおよびイントラチャレンジに必要な登録に関する情報を含むメタデータを持っています。

# 例

## データセットの読み込み

```julia-repl
julia> using MLDatasets

julia> dataset = FAUST()
[ Info: このプログラムはデータ依存性MPI-FAUSTへのアクセスを要求しました
[ Info: システム上で見つかりませんでした。手動インストールが必要です。
┌ Info: データ依存性のロードパスのいずれかのディレクトリにインストールしてください: /home/user/.julia/packages/DataDeps/EDWdQ/deps/data/MPI-FAUST,
│ /home/user/.julia/datadeps/MPI-FAUST,
│ /home/user/.julia/juliaup/julia-1.7.3+0.x86/local/share/julia/datadeps/MPI-FAUST,
│ /home/user/.julia/juliaup/julia-1.7.3+0.x86/share/julia/datadeps/MPI-FAUST,
│ /home/user/datadeps/MPI-FAUST,
│ /scratch/datadeps/MPI-FAUST,
│ /staging/datadeps/MPI-FAUST,
│ /usr/share/datadeps/MPI-FAUST,
└ または /usr/local/share/datadeps/MPI-FAUST
[ Info: 指示に従ってください:
┌ Info: データセット: MPI-FAUST。
└ ウェブサイト: http://faust.is.tue.mpg.de/
インストールが完了したら、'y'を入力して再度読み込みを試みるか、'a'を入力して中止してください
[y/a]
```

今、データセットを指定された場所のいずれかにダウンロードして抽出してください。Unixリンクシステムの場合、例のコマンドは次のようになります。

```bash
unzip -q <path-to-filename</filename.zip ~/.julia/datadeps
```

対応するフォルダーツリーは次のようになります。

```
├── test
│   ├── challenge_pairs
│   └── scans
└── training
    ├── ground_truth_vertices
    ├── registrations
    └── scans
```

`y`を押して再度読み込みを試みてください。

```julia-repl
dataset FAUST:
  scans          =>    100-element Vector{Any}
  registrations  =>    100-element Vector{Any}
  labels         =>    100-element Vector{Vector{Bool}}
  metadata       =>    Dict{String, Any} with 0 entries
```

## トレーニングとテストの分割を読み込む

```julia-repl
julia> train_faust = FAUST(:train)
dataset FAUST:
  scans          =>    100-element Vector{Any}
  registrations  =>    100-element Vector{Any}
  labels         =>    100-element Vector{Vector{Bool}}
  metadata       =>    Dict{String, Any} with 0 entries

julia> test_faust = FAUST(:test)
dataset FAUST:
  scans          =>    200-element Vector{Any}
  registrations  =>    0-element Vector{Any}
  labels         =>    0-element Vector{Vector{Bool}}
  metadata       =>    Dict{String, Any} with 2 entries
```

## スキャン、登録、およびグラウンドトゥルス

```julia-repl
julia> dataset = FAUST(); # デフォルトはトレーニングスプリット

julia> scan = dataset.scans[1] # スキャンを1つ選択
Mesh{3, Float32, Triangle}:
 Triangle(Float32[-0.0045452323, 0.08537669, 0.22134435], Float32[-0.0030340434, 0.08542955, 0.22206494],
Float32[-0.0042151767, 0.08697654, 0.22171047])
 Triangle(Float32[-0.05358432, 0.08490027, 0.17748278], Float32[-0.05379858, 0.083174236, 0.17670263],
Float32[-0.052645437, 0.08346437, 0.17816517])
.
.
.
 Triangle(Float32[-0.07851, -1.0956081, 0.07093428], Float32[-0.06905176, -1.0986279, 0.07775441],
Float32[-0.069199145, -1.0928112, 0.06812464])

julia> registration = dataset.registrations[1] # 対応する登録
Mesh{3, Float32, Triangle}:
 Triangle(Float32[0.12491254, 0.51199615, 0.29041073], Float32[0.11376736, 0.5156298, 0.3007352],
Float32[0.119374536, 0.50043654, 0.29687837])
 Triangle(Float32[0.119374536, 0.50043654, 0.29687837], Float32[0.11376736, 0.5156298, 0.3007352],
Float32[0.10888693, 0.5008964, 0.30557302])
.
.
.
 Triangle(Float32[0.033744745, 0.030968456, 0.2359996], Float32[0.058017172, 0.044458304, 0.23422624],
Float32[0.03615713, 0.04858183, 0.23596591])

julia> label = dataset.labels[1] # スキャン内の各頂点のグラウンドトゥルス/ラベル
176387-element Vector{Bool}:
 1
 1
 1
 .
 .
 .
 0
 0
 0
```

# 参考文献

1. [MPI Faust Website](http://faust.is.tue.mpg.de/)
2. Bogo, Federica & Romero, Javier & Loper, Matthew & Black, Michael. (2014). FAUST: Dataset

and evaluation for 3D mesh registration. Proceedings of the IEEE Computer Society Conference on Computer Vision and Pattern Recognition. 10.1109/CVPR.2014.491.
