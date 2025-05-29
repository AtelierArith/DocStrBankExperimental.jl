```
add_noise!(client::Client, noise_model::NoiseModel)
```

この関数は、指定されたノイズモデルに従って量子システムにノイズを追加します。新しいクライアントと指定されたノイズモデルを引数として `add_noise!` 関数を呼び出します。

# 引数

  * `client::Client`: ノイズが追加されるクライアント。
  * `noise_model::NoiseModel`: 使用されるノイズモデル。

# 例

```julia
client = Client()
noise_model = NoiseModel()
add_noise!(client, noise_model)
```
