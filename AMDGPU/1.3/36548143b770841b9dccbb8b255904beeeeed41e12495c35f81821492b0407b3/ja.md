```
@roc [kwargs...] func(args...)
```

GPU上でカーネルを起動するための高レベルインターフェース。最初の呼び出し時にコンパイルされ、その後の呼び出しではコンパイルされたオブジェクトが再利用されます。

いくつかのキーワード引数がサポートされています：

  * `launch::Bool = true`: カーネルを起動するかどうか。`false`の場合、引数を渡して呼び出すことで起動できるコンパイル済みカーネルを返します。
  * カーネルコンパイルに影響を与える引数、詳細は[`AMDGPU.Compiler.hipfunction`](@ref)を参照してください。
  * カーネル起動に影響を与える引数、詳細は[`AMDGPU.Runtime.HIPKernel`](@ref)を参照してください。
