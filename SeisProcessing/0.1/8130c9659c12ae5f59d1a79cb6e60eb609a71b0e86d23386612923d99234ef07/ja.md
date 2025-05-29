```
SeisGain(in,out,parameters; <キーワード引数>)

トレースのグループを取得します。入力と出力はファイル名です。
```

# 引数

  * `in::String`: 入力ファイル - Seis形式
  * `out::String`: 出力ファイル - Seis形式。
  * `parameters` : 関数SeisGainのキーワード引数のリスト。

# キーワード引数

  * `group="gather"` : オプションはall、someまたはgather
  * `key=["imx","imy"]` : グループのタイプを定義
  * `itrace=1` : 初期トレース番号
  * `ntrace=10000` : 一度に処理するトレースの総数

# 例

```
julia> param = Dict(:dt=>0.01,:kind=>"time",:coef=>[2.0,0.0],:normal=>0)
julia> SeisGain(filein,fileout, param,group="all")
```
