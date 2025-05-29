```
SeisMute(in,out,parameters; <キーワード引数>)
```

ファイル内のトレースの最初の到着前にノイズをミュートします。ミュートされたトレースは出力ファイルに保存されます。ミュート関数は、ソースとレシーバーの間のオフセットおよび最初の層の速度に依存します。t*mute = t*0 + offset/v1。

# 引数

  * `in::String`: 入力ファイル - Seis形式。
  * `out::String`: 出力ファイル - Seis形式。
  * `parameters` : 関数SeisMuteのためのキーワード引数のリスト。

# キーワード引数

  * `group="gather"` : オプションはall、someまたはgather
  * `key=["imx","imy"]` : ギャザーのタイプを定義
  * `itrace=1` : 初期トレース番号
  * `ntrace=10000` : 一度に処理するトレースの総数

# 例

```
julia> param = Dict(:tmute=>0.0, :vmute=>10000, :taper=>0.05,:dt=>0.01)
julia> SeisMute(filein,fileout, param,group="some")
```
