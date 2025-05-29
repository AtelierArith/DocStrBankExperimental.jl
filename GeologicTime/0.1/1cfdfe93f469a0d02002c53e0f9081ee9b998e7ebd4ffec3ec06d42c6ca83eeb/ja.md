# GeologicTime.jl

[![Documentation](https://img.shields.io/badge/docs-stable-blue.svg)](https://Mikumikunisiteageru.github.io/GeologicTime.jl/stable) [![Documentation](https://img.shields.io/badge/docs-dev-blue.svg)](https://Mikumikunisiteageru.github.io/GeologicTime.jl/dev) [![CI](https://github.com/Mikumikunisiteageru/GeologicTime.jl/actions/workflows/CI.yml/badge.svg)](https://github.com/Mikumikunisiteageru/GeologicTime.jl/actions/workflows/CI.yml) [![Codecov](https://codecov.io/gh/Mikumikunisiteageru/GeologicTime.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/Mikumikunisiteageru/GeologicTime.jl) [![Aqua.jl Quality Assurance](https://img.shields.io/badge/Aquajl-%F0%9F%8C%A2-aqua.svg)](https://github.com/JuliaTesting/Aqua.jl)

GeologicTime.jlは、`drawtimescale`関数を使用して特定の時間間隔で地質時代スケールを描画するために主に設計されています。この関数は、手動でインストールしてインポートする必要がある[PyPlot.jl](https://github.com/JuliaPy/PyPlot.jl)に依存しています。

```julia
using GeologicTime
using PyPlot
figure(figsize=(5.4, 0.45))
drawtimescale(100, 0, [3, 4]; fontsize=8, texts = Dict(
	"Cretaceous" => "Cretaceous", "Paleogene" => "Paleogene", 
	"Neogene" => "Neogene", "Quaternary" => "Q", 
	"Late Cretaceous" => "Late Cretaceous", "Paleocene" => "Paleoc.", 
	"Eocene" => "Eocene", "Oligocene" => "Oligoc.", "Miocene" => "Miocene", 
	"Pliocene" => "P", "Pleistocene" => "P"))
gca().set_position([0.02, 0.05, 0.96, 0.9])
savefig("timescale.png", dpi=300)
```

上記のコードは、次の画像を生成します。`drawtimescale`の引数リストでは、`100`と`0`は時間間隔の2つの端を表し、百万年前の時間を示しています；`[3, 4]`は、チャートに期間（コード`3`）と世代（コード`4`）を描画する関数を示しています。

![Geologic time scale from 100 Ma ago to now](https://github.com/Mikumikunisiteageru/GeologicTime.jl/blob/master/docs/illust/imggts.png)

さらに、このパッケージは、`getunit`、`getcolor`、`getstart`、`getstop`、`getspan`、および`getgeotime`などの簡単なルックアップ関数も提供しており、その使用法は[documentation](https://Mikumikunisiteageru.github.io/GeologicTime.jl/dev)で説明されています。これらの関数はPyPlot.jlに依存せず、GeologicTime.jlがロードされると呼び出すことができます。

GeologicTime.jlのコードとドキュメントはMITライセンスの下で公開されています。ただし、すべてのデータは2023年4月23日にアクセスした[Wikipedia](https://en.wikipedia.org/wiki/Geologic_time_scale)の資料に基づいており、CC-SA 3.0ライセンスの下で利用可能です。[data/wikipedia.html](https://github.com/Mikumikunisiteageru/GeologicTime.jl/blob/master/data/wikipedia.html)を含む関連ファイルおよびその派生物[data/timescale.tsv](https://github.com/Mikumikunisiteageru/GeologicTime.jl/blob/master/data/timescale.tsv)のクレジットはWikipediaの貢献者に帰属します。
