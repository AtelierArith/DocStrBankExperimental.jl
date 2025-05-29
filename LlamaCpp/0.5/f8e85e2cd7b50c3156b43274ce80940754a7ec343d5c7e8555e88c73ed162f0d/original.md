```
run_llama(; model::AbstractString, prompt::AbstractString="", nthreads::Int=1, n_gpu_layers::Int=99, ctx_size::Int=2048, args=``)
```

Runs `prompt` through the `model` provided and returns the result. This is a single-turn version of `run_chat`.

See the [full documentation](https://github.com/ggerganov/llama.cpp/blob/master/examples/main/README.md) for more details.

# Arguments

  * `model`: path to the model to be used
  * `prompt`: prompt to be used. Most models expected these to be formatted in a specific way. Defaults to an empty string
  * `nthreads`: number of threads to use. Defaults to the number of available threads
  * `n_gpu_layers`: number of layers to offload on the GPU (a.k.a. `ngl` in llama.cpp). Requires more VRAM on your GPU but can speed up inference. Set to 0 to run inference on CPU-only. Defaults to 99 (=practically all layers)
  * `ctx_size`: context size, ie, how big can the prompt/inference be. Defaults to 2048 (but most models allow 4,000 and more)

Note: If you get odd responses AND you're using an instruction-tuned ("fine-tuned"), it might be that the format of your prompt is not correct.  See HuggingFace's model documentation for the correct prompt format or use a library that will do this for you (eg, PromptingTools.jl)

See also: `run_chat`, `run_server`
