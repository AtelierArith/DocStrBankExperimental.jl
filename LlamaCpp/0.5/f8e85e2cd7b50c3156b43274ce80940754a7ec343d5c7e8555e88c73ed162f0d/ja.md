```
run_llama(; model::AbstractString, prompt::AbstractString="", nthreads::Int=1, n_gpu_layers::Int=99, ctx_size::Int=2048, args=``)
```

指定された`model`を通じて`prompt`を実行し、結果を返します。これは`run_chat`の単一ターン版です。

詳細については[完全なドキュメント](https://github.com/ggerganov/llama.cpp/blob/master/examples/main/README.md)を参照してください。

# 引数

  * `model`: 使用するモデルへのパス
  * `prompt`: 使用するプロンプト。ほとんどのモデルは特定の形式でのフォーマットを期待します。デフォルトは空の文字列です
  * `nthreads`: 使用するスレッドの数。デフォルトは利用可能なスレッドの数です
  * `n_gpu_layers`: GPUにオフロードするレイヤーの数（llama.cppの`ngl`とも呼ばれます）。GPUのVRAMを多く必要としますが、推論を高速化できます。CPUのみで推論を実行するには0に設定します。デフォルトは99（ほぼすべてのレイヤー）
  * `ctx_size`: コンテキストサイズ、つまりプロンプト/推論の大きさ。デフォルトは2048（ただし、ほとんどのモデルは4,000以上を許可します）

注意: 奇妙な応答が返ってきた場合、かつ指示調整された（「ファインチューニングされた」）モデルを使用している場合、プロンプトの形式が正しくない可能性があります。正しいプロンプト形式についてはHuggingFaceのモデルドキュメントを参照するか、これを行うライブラリ（例: PromptingTools.jl）を使用してください。

関連: `run_chat`, `run_server`
