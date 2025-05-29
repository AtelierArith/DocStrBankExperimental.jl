```
detect_chimeras_from_files(V_fasta::String, assignments::String, out::String;

        p_threshold::Float64 = 0.95,
        receptor::String = "IG",

        non_chimeric_MiAIRR::Union{String, Nothing} = nothing,
        chimeric_MiAIRR::Union{String, Nothing} = nothing,
        chimeric_alignments::Union{String, Nothing} = nothing,
        recombfreqplot::Union{String, Nothing} = nothing,
        detailed::Bool = false,
        subsample::Union{Int, Nothing} = nothing,
        deduplicate::Bool = false,
        chunk_size::Union{Int, Nothing} = nothing,

        HMM_parameters::Union{String, Nothing} = nothing,
        mafft::Union{String, Nothing} = nothing,
        align_database::Bool = false,
        count_chimeric_segments::Bool = false,
        trim::Int = 5,
        seed::Int = 123,

        quiet::Bool = false,
        disable_internal_dedup::Bool = false
        )
```

入力ファイルからCHMMAIRRaを実行し、出力ファイルに書き込む際のI/Oに注意します。

# 引数:

  * `V_fasta::String`: fasta形式のVデータベース。
  * `assignments::String`: MiAIRR形式のVDJ割り当て。
  * `out::String`: CHMMAIRRaの出力を書き込む。

# オプション引数:

  * `p_threshold::Float64`: スイッチングテンプレートの事後閾値。
  * `receptor::String`: 実行する適応免疫受容体。オプション: IG, TCR。
  * `non_chimeric_MiAIRR::Union{String, Nothing}`: 非キメラと判断された配列の割り当てを書き込む。
  * `chimeric_MiAIRR::Union{String, Nothing}`: キメラと判断された配列の割り当てを書き込む。
  * `chimeric_alignments::Union{String, Nothing}`: キメラ配列とそれに一致した祖先配列を含むfastaファイルを書き込む。
  * `recombfreqplot::Union{String, Nothing}`: 再結合イベントごとのキメラのプロットを生成する。
  * `detailed::Bool`: キメラに関する詳細を含める。キメラ配列のためにviterbiパスを計算し、startingpoint、recombinations、recombinations*degapped、およびmax*log_prob列を追加する。
  * `subsample::Union{Int, Nothing}`: キメラ検出を実行するためにこの数のユニークな配列をランダムにサブサンプリングする。
  * `deduplicate::Bool`: v*sequence*alignment列によって入力を重複排除する。サブサンプルが指定されている場合、重複排除の後にサブサンプリングが行われることに注意。
  * `chunk_size::Union{Int, Nothing}`: 一度にchunk_size行の入力を読み込み、そのチャンクの出力を書き込み、次のチャンクに移動する。
  * `HMM_parameters::Union{String, Nothing}`: 設定されている場合、このファイルのHMMパラメータを使用する。–receptorからのパラメータプリセットを上書きします。フォーマットについてはsrc/IG*parameters.tsvまたはsrc/TCR*parameters.tsvを参照してください。
  * `mafft::Union{String, Nothing}`: MAFFTバイナリへのパス。提供されていない場合、システムのPATH内でmafftを探そうとします。
  * `align_database::Bool`: データベースV配列をアラインするかどうか。
  * `count_chimeric_segments::Bool`: 設定されている場合、非キメラ配列に出現するキメラセグメントの数をカウントする。chimera*segment*counts列を追加します。
  * `trim::Int`: 非キメラ配列での一致を検索する際にキメラセグメントの内側の端から切り取るヌクレオチドの数。
  * `seed::Int`: ランダムサブサンプリングに使用するシード。
  * `quiet::Bool`: 設定されている場合、エラーメッセージ以外のメッセージを非表示にする。
  * `disable_internal_dedup::Bool`: 設定されている場合、内部で配列を重複排除しない。これはタイミングベンチマーク目的で追加され、出力には影響しません。
