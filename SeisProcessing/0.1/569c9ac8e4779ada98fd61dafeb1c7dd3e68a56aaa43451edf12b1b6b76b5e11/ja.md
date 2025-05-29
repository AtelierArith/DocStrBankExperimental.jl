```
  SeisProcessFile(in1,in2,out,operators,parameters;<keyword arguments>)
```

2つのファイルから読み込み、ディスクに書き込む処理フローを実行します。

# 引数

  * `in1::String`: 入力ファイル名 - Seis形式。
  * `in2::String`: 入力ファイル名 - Seis形式。
  * `out::String`: 出力ファイル名 - Seis形式。
  * `operators`
  * `parameters`

# キーワード引数

  * `group="gather"` : オプションは all, some または gather
  * `key=["imx","imy"]` : ギャザーのタイプを定義
  * `itrace=1` : 初期トレース
  * `ntrace=10000` : 一度に処理するトレースの総数

# 例

ショットギャザーによって、地震キューブにバンドパスフィルターを順次適用します。dtは0.002と仮定します。

```
julia> operators = [SeisBandPass]
julia> param = [Dict(:dt=>0.002, :fa=>20,:fb=>30,:fc=>80,:fd=>90)]
julia> SeisProcessFile(filein,fileout,operators,param,key=["sx"])
```
