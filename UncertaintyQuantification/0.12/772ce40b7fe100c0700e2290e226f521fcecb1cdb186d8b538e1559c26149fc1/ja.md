```
SlurmInterface(options::Dict{String,String}, throttle::Integer, btachsize::Integer, extras::Vector{String})
```

`SlurmInterface`が`ExternalModel`に渡されると、モデル評価はslurmジョブ配列を使用して実行されます。これにより、Juliaのネイティブな並列処理に依存することなく、より重いシミュレーションやワークフローをサンプリングできます。`SlurmInterface`は自動的にslurmジョブ配列スクリプトを生成し、Juliaはこのジョブが完了するのを待ってから結果を抽出します。

`SlurmInterface`を使用する場合、`addprocs(N)`でJuliaにワーカーをロードする必要はなく、個々のモデル評価に必要なノード/タスクを要求することもありません。`extras`を使用して、モデルを実行するために事前にロードする必要があるもの（たとえば、モジュールのロード）を指定します。

`throttle`は、ジョブ配列内で同時に実行されるシミュレーションの数を指定します。つまり、`N=1000`サンプルで`MonteCarlo`シミュレーションを実行する場合、`throttle=200`では、合計1000回のシミュレーションが実行されますが、同時に実行されるのは200回だけです。HPCスケジューラ（および管理者）は、同時に要求するジョブが多すぎると不満を持つかもしれません。空のままにすると、スケジューラのデフォルトのスロットが使用されます。HPCマシンが提出されたジョブ配列のサイズを制限する場合、提出を小さな「バッチ」に分割できます。「batchsize」を指定して、ジョブ配列の最大サイズを設定します。これは、実行回数の合計を変更するものではありません。

# パラメータ

```
options   : slurmスクリプトに追加するSBATCHオプションの辞書
throttle  : 同時に実行されるジョブの数
batchsize : slurm配列の最大サイズ、HPCが配列内のジョブ数を制限する場合に使用
extras    : モデルが実行される前に実行される指示、例：python環境のアクティブ化やモジュールのロード
```

# 例

```jldoctest
julia> slurm = SlurmInterface(Dict("account" => "HPC_account_1", "partition" => "CPU_partition"), extras = ["load python3"])
SlurmInterface(Dict("account" => "HPC_account_1", "partition" => "CPU_partition"), 0, 0, ["load python3"])
```
