```
detect_chimeras(refnames::Vector{String}, refseqs::Vector{String}, assignments::DataFrame;
                HMM_parameters::Union{Dict, Nothing} = nothing,
                p_threshold::Float64 = 0.95,
                receptor::String = "IG",

                chimeric_alignments::Bool = false,
                recombfreqplot::Bool = false,
                detailed::Bool = false,
                subsample::Union{Int, Nothing} = nothing,
                deduplicate::Bool = false,

                count_chimeric_segments::Bool = false,
                trim::Int = 5,
                seed::Int = 123,

                mafft::Union{String, Nothing} = nothing,
                align_database::Bool = false,

                quiet::Bool = false,
                disable_internal_dedup::Bool = false
                )::NamedTuple{(:out, :chimeric_alignments, :recombfreqplot),
                            Tuple{DataFrame,
                            Union{Nothing, Tuple{Vector{String}, Vector{String}}},
                            Any}
                            }
                }
```

CHMMAIRRaを解析された引数で実行し、関連する出力を含むタプルとして出力を返します。出力タプルのフィールド：

1. out: チメリズム確率を持つ入力アサインメントデータフレーム。
2. chimeric*alignments: どの参照配列がどの位置で再結合して検出されたチメラを形成したかを示すアライメントの名前と配列。chimeric*alignmentsがfalseの場合はnothingに設定されます。
3. recombfreqplot: 期待される頻度で正規化された最も頻繁な再結合の棒グラフ。recombfreqplotがfalseの場合はnothingに設定されます。

# 引数：

  * `refnames::Vector{String}`: 参照配列の名前。
  * `refseqs::Vector{String}`: 参照配列の配列。
  * `assignments::DataFrame`: MiAIRR形式のVDJアサインメント。

# オプション引数：

  * `HMM_parameters::Union{Dict, Nothing}`: 設定されている場合、この辞書のHMMパラメータを使用します。受容体からのパラメータプリセットを上書きします。
  * `p_threshold::Float64`: テンプレートの切り替えの事後閾値。
  * `receptor::String`: 実行する適応免疫受容体。オプション: IG, TCR。
  * `chimeric_alignments::Bool`: チメリック配列とそれに一致した原始配列のアライメントを生成して返すかどうか。
  * `recombfreqplot::Bool`: 再結合イベントごとのチメリズムのプロットを生成して返すかどうか。
  * `detailed::Bool`: チメラに関する詳細を含めるかどうか。チメリック配列のためにビタービパスを計算し、startingpoint、recombinations、recombinations*degapped、およびmax*log_prob列を追加します。
  * `subsample::Union{Int, Nothing}`: チメラ検出を実行するためにこの数のユニークな配列をランダムにサブサンプリングします。
  * `deduplicate::Bool`: v*sequence*alignment列によって入力を重複排除するかどうか。サブサンプルが指定されている場合、重複排除の後にサブサンプリングが行われることに注意してください。
  * `count_chimeric_segments::Bool`: 設定されている場合、非チメリック配列に出現するチメリックセグメントの数をカウントします。chimera*segment*counts列を追加します。
  * `trim::Int`: 非チメリック配列での一致を検索する際に、チメリックセグメントの内側の端から切り取るヌクレオチドの数。
  * `seed::Int`: ランダムサブサンプリングに使用するシード。
  * `mafft::Union{String, Nothing}`: MAFFTバイナリへのパス。提供されていない場合、システムPATH内でmafftを見つけようとします。
  * `align_database::Bool`: データベースV配列をアライメントするかどうか。
  * `quiet::Bool`: 設定されている場合、エラーメッセージ以外のメッセージを非表示にします。
  * `disable_internal_dedup::Bool`: 設定されている場合、内部で配列を重複排除しません。これはタイミングベンチマーク目的で追加され、出力には影響しません。
