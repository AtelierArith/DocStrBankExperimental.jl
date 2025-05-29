```
SeisNMO(in,out,parameters; <キーワード引数>)
```

# 引数

  * `in::String`: 入力ファイル - Seis形式。
  * `out::String`: 出力ファイル - Seis形式。
  * `parameters` : 関数SeisMuteのためのキーワード引数のリスト。

# キーワード引数

  * `group="gather"` : オプションはall、someまたはgather
  * `key=["imx","imy"]` : ガザーのタイプを定義
  * `itrace=1` : 初期トレース番号
  * `ntrace=10000` : 一度に処理するトレースの総数

# 例

```
julia> param = Dict(:tmute=>0.0, :vmute=>10000, :taper=>0.05,:dt=>0.01)
julia> SeisMute(filein,fileout, param,group="some")
```
