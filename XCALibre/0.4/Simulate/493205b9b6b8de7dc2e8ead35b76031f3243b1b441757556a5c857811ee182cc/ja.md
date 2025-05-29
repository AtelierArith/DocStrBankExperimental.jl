```
hardware = set_hardware(backend, workgroup)
```

バックエンドを構成するために使用される関数。

# 入力

  * `backend` バックエンドを指定するために使用される名前付きタプル。例: `CPU()`, `CUDABackend()` または `KernelAbstraction.jl` によってサポートされている他のバックエンド。
  * `workgroup::Int` これは並列実行で協力するワーカーの数を指定する整数です。GPUの場合、デバイスのワープのサイズに設定することができます。例: `workgroup = 32`。CPUでは、`KernelAbstractions.jl` のデフォルト値は現在 `workgroup = 1024` です。

# 出力

この関数は、`backend` と `workgroup` のフィールドを持つ `NamedTuple` を返します。これらは `XCALibre.jl` 内部でアクセスされ、指定されたカーネルを実行します。
