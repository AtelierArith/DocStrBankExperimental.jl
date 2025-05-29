```
  SeisProcessFile(in,out,operators,parameters;<keyword arguments>)
```

ディスクから読み書きする処理フローを実行します。

fは次の構文を持つ関数です: d2 = f(d1,param)、ここでparamは関数のキーワード引数のリストです。fは関数のベクトルである可能性があります。それらは同じトレースのグループに対して順次実行されます。

# 引数

  * `in`: Seis形式のStringまたはArray{String,1}型の入力ファイル名
  * `out`: Seis形式のStringまたはArray{String,1}型の出力ファイル名
  * `operators`
  * `parameters`

# キーワード引数

  * `group="gather"` : オプションはall, someまたはgather
  * `key=["imx","imy"]` : ギャザーのタイプを定義
  * `itrace=1` : 初期トレース
  * `ntrace=10000` : 一度に処理するトレースの総数

# 例

ショットギャザーごとに順次、地震キューブにバンドパスフィルターを適用します。dtは0.002と仮定します。

```
julia> operators = [SeisBandPass]
julia> param = [Dict(:dt=>0.002, :fa=>20,:fb=>30,:fc=>80,:fd=>90)]
julia> SeisProcessFile(filein,fileout,operators,param,key=["sx"])
```
