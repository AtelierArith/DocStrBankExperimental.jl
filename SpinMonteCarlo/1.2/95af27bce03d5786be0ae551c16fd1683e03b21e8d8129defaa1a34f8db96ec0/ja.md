```
runMC(param::Parameter)
runMC(params::AbstractArray{Parameter}
      ;
      parallel::Bool=false,
      autoID::Bool=true)
```

モンテカルロシミュレーションを実行し、計算された観測量を返します。

# 再起動

`"$(param["Checkpoint Filename Prefix"])_$(param["ID"]).dat"`という名前のチェックポイントファイルが存在し、`param["Checkpoint Interval"] > 0.0`の場合、`runMC`はこのファイルを読み込み、保留中のシミュレーションを再起動します。注意: 再起動は、juliaのバージョンまたはシステムイメージが変更された場合に失敗します（`Serialization.serialize`のドキュメントを参照してください）。

# キーワード引数

  * `autoID`: trueの場合、`"ID"`が設定（上書き）されます `params[i]["ID"] = i`。
  * `parallel`: trueの場合、シミュレーションを並行して実行します（`map`の代わりに`pmap`を使用します）。

# `param`に必要なキー

  * "Model"
  * "Lattice"
  * "Update Method"

# `param`にオプションのキー

  * "MCS": 熱化後のモンテカルロステップ数

      * デフォルト: `8192`
  * "Thermalization": 熱化のためのモンテカルロステップ数

      * デフォルト: `MCS>>3`
  * "Binning Size": ビンのサイズ

      * デフォルト: `0`
  * "Number of Bins": ビンの数

      * デフォルト: `0`
      * "Binning Size"と"Number of Bins"の両方が指定されていない場合、"Binning Size"は`floor(sqrt(MCS))`に設定されます。
  * "Seed": 擬似乱数生成器`MersenneTwister`の初期シード

      * デフォルト: ランダムに決定されます（`Random.seed!`のドキュメントを参照してください）。
  * "Checkpoint Filename Prefix": "再起動"セクションを参照してください。

      * デフォルト: `"cp"`
  * "ID": "再起動"セクションを参照してください。

      * デフォルト: `0`
  * "Checkpoint Interval": チェックポイントファイルを書き込む間隔（秒）。

      * デフォルト: `0.0`、これはチェックポイントファイルが読み込まれず、保存されないことを意味します。
