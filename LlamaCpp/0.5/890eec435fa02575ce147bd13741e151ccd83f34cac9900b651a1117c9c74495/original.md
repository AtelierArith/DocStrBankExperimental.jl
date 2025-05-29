```
run_server(; model::AbstractString, host::AbstractString="127.0.0.1", port::Int=10897, nthreads::Int=Threads.nthreads(), 
n_gpu_layers::Int=99, ctx_size::Int=2048, args=``)
```

Starts a simple HTTP server with the `model` provided.

Open `http://{host}:{port}` in your browser to interact with the model or use an HTTP client to send requests to the server.

Interrupt the server with `Ctrl+C`.

# Arguments

  * `model`: path to the model to be used
  * `host`: host address to bind to. Defaults to "127.0.0.1"
  * `port`: port to listen on. Defaults to 10897
  * `nthreads`: number of threads to use. Defaults to the number of available threads
  * `n_gpu_layers`: number of layers to offload on the GPU (a.k.a. `ngl` in llama.cpp). Requires more VRAM on your GPU but can speed up inference. Set to 0 to run inference on CPU-only. Defaults to 99 (=practically all layers)
  * `ctx_size`: context size, ie, how big can the prompt/inference be. Defaults to 2048 (but most models allow 4,000 and more)
  * `embeddings`: whether to allow generating of embeddings. Defaults to `false`.  Note: Embeddings are not supported by all models and it might break the server!
  * `args`: additional arguments to pass to the server

See the [full documentation](https://github.com/ggerganov/llama.cpp/blob/master/examples/server/README.md) for more details.

# Example

```julia using LlamaCpp

# Download a model from HuggingFace, eg, Phi-2.

# See details [here](https://huggingface.co/TheBloke/dolphin-2_6-phi-2-GGUF)

using Downloads model = joinpath("models", "dolphin-2*6-phi-2.Q6*K.gguf") mkpath(dirname(model)) # ensure the folder exists Downloads.download("https://huggingface.co/TheBloke/dolphin-2*6-phi-2-GGUF/resolve/main/dolphin-2*6-phi-2.Q6_K.gguf", model)

# go make a cup of tea while you wait... this is a 2.3GB download

# Start the server

run_server(; model)
