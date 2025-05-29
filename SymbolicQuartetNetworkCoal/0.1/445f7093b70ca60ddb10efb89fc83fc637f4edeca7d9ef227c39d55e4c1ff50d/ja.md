```
network_expectedCF_formulas(network::HybridNetwork; 
                            showprogressbar=true, 
                            inheritancecorrelation=0, 
                            filename="symbolicQNC-HFO-out"::AbstractString, 
                            symbolic=false::Bool, 
                            savecsv=false::Bool, 
                            macaulay=false::Bool, 
                            matlab=false::Bool, 
                            multigraded=false::Bool)
```

系統的ネットワークにおける四元数の期待された一致係数（CF）を計算し、オプションで記号的な式を生成します。

この関数は、`HybridNetwork`内のすべての可能な四元数の期待された一致係数（CF）を計算し、共alescentプロセスとハイブリッドノードでの相続相関を考慮します。数値モード（デフォルト）または記号モード（`symbolic=true`の場合）で動作し、CFを枝の長さと相続パラメータ（γ）を含む式として表現します。結果はファイルに記録され、オプションの出力はCSV、Macaulay2、MATLAB、または多重グレーディングの暗黙化ファイルとして保存できます。

# 引数

  * `network::HybridNetwork`: PhyloNetworksパッケージからの系統ネットワークで、共alescent単位のエッジ長とハイブリッドエッジのγ値を持ちます。
  * `showprogressbar::Bool=true`: 真の場合、四元数計算の進行状況バーを表示します。
  * `inheritancecorrelation::Number=0`: ハイブリッドノードでの相続確率間の相関（0と1の間でなければなりません）。
  * `filename::AbstractString="symbolicQNC_HFO_out"`: 出力ファイルの基本名（例：ログ、CSV、Macaulay2、MATLAB）。
  * `symbolic::Bool=false`: 真の場合、CFを記号的な式として計算します。すべてのエッジパラメータが定義されている必要があるか、ランダムな値が割り当てられます。
  * `savecsv::Bool=false`: 真の場合、CFを`<filename>.csv`という名前のCSVファイルに保存します。
  * `macaulay::Bool=false`: 真の場合、記号的分析のためのMacaulay2スクリプト（`<filename>.m2.txt`）を生成します。`symbolic=true`が必要です。
  * `matlab::Bool=false`: 真の場合、記号的分析のためのMATLABスクリプト（`<filename>.m`）を生成します。`symbolic=true`が必要です。
  * `multigraded::Bool=false`: 真の場合、Macaulay2の多重グレーディングの暗黙化スクリプト（`<filename>.im.m2.txt`）を生成します。`symbolic=true`が必要です。

# 戻り値

  * `quartet::Vector{PhyloNetworks.QuartetT}`: 四元数のインデックス、分類群、およびCF（数値または記号）を含むQuartetTオブジェクトの配列。
  * `taxa::Vector{String}`: ネットワークからの分類群名のソートされたリスト。

# 例外をスロー

  * `ErrorException`: ルートが葉である場合、エッジの長さが欠落している/負である場合、γ値が欠落している/負である場合、または相続相関が無効な場合。
  * `ErrorException`: `macaulay`または`matlab`が真であるが`symbolic`が偽である場合。

# 副作用

  * トポロジー、パラメータ、およびCFを含むログファイル（`<filename>.log`）を書き込みます。
  * フラグに基づいてCSV、Macaulay2、MATLAB、または多重グレーディングのファイルをオプションで書き込みます。
