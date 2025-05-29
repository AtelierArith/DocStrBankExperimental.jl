```
gensave_snapshot!(io, model, T, [N=1])
gensave_snapshot!(filename, model, T, [N=1])
```

`N` のスナップショットを `io` または `filename` に生成して書き込みます。

# 引数

  * `io::IO` : スナップショットが書き込まれる出力ストリーム
  * `filename::String` : スナップショットが書き込まれるファイルの名前
  * `model::Model` : シミュレーションされるモデル
  * `T::Real` : 温度
  * `N::Integer=1` : 生成されるスナップショットの数
  * `MCS::Integer=1` : スナップショット生成に続くモンテカルロステップの数
  * `sep::String=" "` : スナップショットのフィールドセパレーター
