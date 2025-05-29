```
readABF(::Type{T}, FORMAT::Type, abf_data::Union{String,Vector{UInt8}};
    trials::Union{Int64,Vector{Int64}}=-1,
    channels::Union{Int64, String, Vector{String}, Nothing}=nothing,
    average_trials::Bool=false,
    stimulus_name::Union{String, Vector{String}, Nothing}=nothing,
    stimulus_threshold::T=2.5,
    warn_bad_channel=false,
    flatten_episodic::Bool=false,
    time_unit=:s
) where {T<:Real}
```

Axon Binary Format (ABF) ファイルを読み取り、解析し、電気生理学データと関連メタデータを含む Experiment オブジェクトを返します。

# 引数

  * `T`: データの数値型（例：Float32、Float64）
  * `FORMAT`: 実験のフォーマットタイプ
  * `abf_data`: ABFファイルへのファイルパスまたは生のABFデータをバイトベクターとして

# オプション引数

  * `trials`: 試行の選択

      * `-1`: すべての試行（デフォルト）
      * `Int64`: 単一の試行
      * `Vector{Int64}`: 複数の特定の試行
  * `channels`: チャンネルの選択

      * `nothing`: すべてのチャンネル（デフォルト）
      * `Int64`: インデックスによる単一のチャンネル
      * `String`: 名前による単一のチャンネル
      * `Vector{String}`: 名前による複数のチャンネル
  * `average_trials`: 試行を平均化するかどうか（デフォルト：false）
  * `stimulus_name`: 刺激チャンネルの名前

      * `nothing`: 刺激なし（デフォルト）
      * `String`: 単一の刺激チャンネル
      * `Vector{String}`: 複数の刺激チャンネル
  * `stimulus_threshold`: デジタル刺激イベントを検出するための閾値（デフォルト：2.5）
  * `warn_bad_channel`: 無効なチャンネルについて警告するかどうか（デフォルト：false）
  * `flatten_episodic`: エピソードデータを連続データにフラット化するかどうか（デフォルト：false）
  * `time_unit`: データの時間単位

      * `:s`: 秒（デフォルト）
      * `:ms`: ミリ秒

# 戻り値

  * 次を含む Experiment オブジェクト：

      * 生データ配列
      * 時間ベクター
      * チャンネル名と単位
      * 刺激プロトコル（指定されている場合）
      * HeaderDict における元の ABF メタデータ

# チャンネル命名規則

1. ADC チャンネル: 録音からの正確な名前を使用（例："Vm_prime", "IN 7"）
2. アナログチャンネル: "A1", "A2" などまたは "Analog 1", "Analog 2" など
3. デジタルチャンネル: "D1", "D2" などまたは "Digital 1", "Digital 2" など

# 例

```julia
# 基本的な使用法 - すべてのチャンネルと試行を読み取る
exp = readABF(Float32, "path/to/file.abf")

# 特定のチャンネルを読み取り、試行を平均化
exp = readABF(Float32, "path/to/file.abf",
    channels=["Vm_prime", "IN 7"],
    average_trials=true)

# 刺激抽出を伴う読み取り
exp = readABF(Float32, "path/to/file.abf",
    stimulus_name="Digital 1",
    stimulus_threshold=2.5)

# 特定の試行を読み取り、エピソードデータをフラット化
exp = readABF(Float32, "path/to/file.abf",
    trials=1:5,
    flatten_episodic=true)

# ミリ秒単位で読み取り
exp = readABF(Float32, "path/to/file.abf",
    time_unit=:ms)
```

参照： [`parseABF`](@ref), [`getWaveform`](@ref), [`extractStimulus`](@ref)
