```
run_server(; model::AbstractString, host::AbstractString="127.0.0.1", port::Int=10897, nthreads::Int=Threads.nthreads(), 
n_gpu_layers::Int=99, ctx_size::Int=2048, args=``)
```

提供された`model`でシンプルなHTTPサーバーを起動します。

ブラウザで`http://{host}:{port}`を開いてモデルと対話するか、HTTPクライアントを使用してサーバーにリクエストを送信します。

`Ctrl+C`でサーバーを中断します。

# 引数

  * `model`: 使用するモデルのパス
  * `host`: バインドするホストアドレス。デフォルトは"127.0.0.1"
  * `port`: リッスンするポート。デフォルトは10897
  * `nthreads`: 使用するスレッドの数。デフォルトは利用可能なスレッドの数
  * `n_gpu_layers`: GPUにオフロードするレイヤーの数（llama.cppでは`ngl`として知られています）。GPUのVRAMを多く消費しますが、推論を高速化できます。CPUのみで推論を実行するには0に設定します。デフォルトは99（実質的にすべてのレイヤー）
  * `ctx_size`: コンテキストサイズ、つまりプロンプト/推論の大きさ。デフォルトは2048（ただし、ほとんどのモデルは4,000以上を許可します）
  * `embeddings`: 埋め込みの生成を許可するかどうか。デフォルトは`false`。注意: 埋め込みはすべてのモデルでサポートされているわけではなく、サーバーが壊れる可能性があります！
  * `args`: サーバーに渡す追加の引数

詳細については[完全なドキュメント](https://github.com/ggerganov/llama.cpp/blob/master/examples/server/README.md)を参照してください。

# 例

```julia using LlamaCpp

# HuggingFaceからモデルをダウンロードします。例: Phi-2。

# 詳細は[こちら](https://huggingface.co/TheBloke/dolphin-2_6-phi-2-GGUF)を参照してください。

using Downloads model = joinpath("models", "dolphin-2*6-phi-2.Q6*K.gguf") mkpath(dirname(model)) # フォルダーが存在することを確認します Downloads.download("https://huggingface.co/TheBloke/dolphin-2*6-phi-2-GGUF/resolve/main/dolphin-2*6-phi-2.Q6_K.gguf", model)

# 待っている間にお茶を入れに行きましょう... これは2.3GBのダウンロードです

# サーバーを起動します

run_server(; model)
```
