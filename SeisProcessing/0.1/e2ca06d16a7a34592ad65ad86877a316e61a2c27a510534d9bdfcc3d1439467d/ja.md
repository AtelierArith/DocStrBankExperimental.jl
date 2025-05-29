```
SeisBandPass(in,out,parameters; <キーワード引数>)
```

# 引数

  * `in::String`: 入力ファイル - Seis形式
  * `out::String`: 出力ファイル - Seis形式。
  * `parameters` : 関数SeisBandPassのためのキーワード引数のリスト。

# キーワード引数

  * `group="gather"` : オプションはall、someまたはgather
  * `key=["imx","imy"]` : ギャザーのタイプを定義
  * `itrace=1` : 初期トレース番号
  * `ntrace=10000` : 一度に処理するトレースの総数

# 例

```
julia> param = Dict(:fa>=0,:fb=>0,:fc=>60,:fd=>80)
julia> SeisBandPass(filein,fileout, param,group="all")
```
