```julia
Simulation(directory::AbstractString, model_info::Dict)

```

シリアライズされたディレクトリからSimulationを構築します。呼び出し元は、元のSimulationに渡した任意のkwargsをここに渡す必要があります。

# 引数

  * `directory::AbstractString`: serializeの呼び出しから返されたディレクトリ
  * `model_info::Dict`: シリアライズできないモデルパラメータを含む二層の辞書。外側の辞書は問題名でキー付けされるべきです。内側の辞書には'optimizer'が含まれ、'jump_model'を含むこともできます。これらは元のシミュレーションで使用されたのと同じ値である必要があります。
