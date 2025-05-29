```
gridtopology(;kwargs...)
```

入力データを分析することでネットワークトポロジーを発見する`function`です。

生の入力データに基づくトポロジーグラフ（入力トポロジー）と、分散負荷や開閉スイッチなどの特定の特性に基づく別のトポロジーグラフ（作業トポロジー）を提示します。作業トポロジーは`powerflow()`関数で使用されるトポロジーです。

データは最小限の仕様を持つ`.cvs`ファイルを介して入力され、分散負荷のための中間点を示す必要はありません。`gridtopology()`は、分散負荷をシミュレートするために、線分の中間にダミーバスを自動的に作成します。

x,yバス位置情報なしでトポロジーグラフを表示することもできます。

# キーワード引数

```jldoctest
    input::String=""
    output::String=""
    save_topology::Bool=true
    display_topology::Bool=false
    display_topology::Bool=false
    graph_title::String=""
    marker_size::Float64=1.5
    timestamp::Bool=false
```

# データファイル

以下のファイルは入力ディレクトリに存在する必要があります：

```jldoctest
    substation.csv
    line_segments.csv
    line_configurations.csv
```

必要に応じて、以下のファイルも入力ディレクトリに存在する必要があります：

```jldoctest
    transformers.csv
    regulators.csv
    switches.csv
    distributed_loads.csv
```

以下のファイルはオプションです：`bus_coords.csv`

`powerflow()`関数によって必要とされる他のファイルもありますが、`gridtopology()`の操作には必要ありません。

# 注意事項

`input="somewhere"`を使用して、入力ファイルがあるディレクトリを指定します。ディレクトリが存在しない場合、`gridtopology()`は警告を出し、実行を停止します。

`output="somewhere"`を使用して、入力結果が書き込まれるディレクトリを指定します。ディレクトリが存在しない場合、`gridtopology()`によって作成されます。

デフォルトでは、`gridtopology()`はコンピュータ画面にトポロジーグラフを表示しません。自動的に表示するには、`gridtopology(display_topology=true)`が必要です。

グラフのタイトル、マーカーサイズ、タイムスタンプなどのグラフィック属性を変更できます。キーワード引数はカンマで区切る必要があります。

# 例：

```jldoctest
gridtopology(input="examples/ieee-34", output="results", display_topology=true, graph_title="ieee 34 node test feeder", marker_size=12, timestamp=true)
```

ここで`gridtopology()`は、相対ディレクトリexamples/ieee-34にある構成ファイルによって指定されたネットワークのトポロジーを発見します。2つのpng画像ファイルがresultsという名前のディレクトリに保存され、そのファイル名には作成日時のサフィックスが付加されます。トポロジー画像は指定されたタイトルで画面にも表示されます。バスインジケーターの円マーカーは相対サイズ12になります。
