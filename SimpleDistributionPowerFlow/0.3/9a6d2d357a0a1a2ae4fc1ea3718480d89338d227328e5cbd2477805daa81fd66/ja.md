```
powerflow(;kwargs...)
```

三相配電ネットワークの電圧レベルとバス間のラインの電力フローを、グリッドインフラストラクチャ、負荷、発電情報に基づいて評価するための `function` です。    

データは、最小限の仕様を持つ `.cvs` ファイルを介して入力されます。分散負荷の中間点を示したり、バスの連続列挙を行う必要はありません。`powerflow()` は `gridtopology()` を活用してネットワークトポロジーを発見します。スイッチの開閉によるトポロジーの変化に応じて、バス電圧を評価し、逆電力フローを計算できます。

# キーワード引数

```jldoctest
    input::String=""
    output::String=""
    tolerance::Float64=1e6
    max_iterations::Int=30
    display_summary::Bool=true
    save_topology::Bool=false
    display_topology::Bool=false
    graph_title::String=""
    marker_size::Float64=1.5
    timestamp::Bool=false
    verbose::Bool=0
```

# データファイル

以下のファイルは入力ディレクトリに存在する必要があります：

```jldoctest
    substation.csv
    line_segments.csv
    line_configurations.csv
    spot_loads.csv
```

必要に応じて、以下のファイルも入力ディレクトリに存在する必要があります：

```jldoctest
    transformers.csv
    regulators.csv
    switches.csv
    capacitors.csv
    distributed_loads.csv
    distributed_generation.csv
```

以下のファイルはオプションです：`bus_coords.csv`

# 注意事項

デフォルトでは、`powerflow()` は入力ファイルを現在のディレクトリから読み込み、結果ファイルを現在のディレクトリに書き込みます。ユーザーが他のディレクトリからファイルを読み込みたい場合は、入力引数で指定する必要があります。また、結果ファイルを他のディレクトリに保存したい場合は、出力引数で指定する必要があります。

デフォルトでは、実行後にコンピュータ画面に総入力および損失電力の要約とバス電圧の結果が表示され、他の結果は出力ディレクトリの .csv ファイルに保存されます。

結果ファイルには、逐次分析のためのタイムスタンプを含めることができます。

現在、`powerflow()` はラジアルフィーダーでのみ動作し、ユーザーはスイッチの状態を変更してループを開くことができます。

運用アルゴリズムは、William H. Kersting によって提案された一般化行列を用いた前方-後方スイープに基づいており、Distribution System Modeling and Analysis, 4th ed, Taylor & Francis Group 2017 に記載されています。

# 例：

```jldoctest
powerflow(input="examples/ieee-34", output="results", tolerance=1e-9, max_iterations=30, display_topology=true, 
          graph_title="ieee 34 node test feeder", marker_size=12, timestamp=true)
```

ここで `powerflow()` は、内部的に `gridtopology()` 関数を呼び出し、指定されたネットワークのトポロジーをターミナルの画面に表示し、計算された変電所電圧が元の値から 1e-9 未満の差になるか、30 回の反復が達成されるまで前方および後方スイープを実行します。
