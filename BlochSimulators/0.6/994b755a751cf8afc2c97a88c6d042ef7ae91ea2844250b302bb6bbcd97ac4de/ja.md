```
simulate_magnetization(resource, sequence, parameters)
```

すべての組み合わせの組織特性に対する磁化応答（通常はエコー時間での横磁化で、空間エンコーディング勾配が適用されていない）をシミュレートします。

この関数は、MRフィンガープリンティングの目的で辞書を生成するためにも使用できます。

# 引数

  * `resource::AbstractResource`: `CPU1()`, `CPUThreads()`, `CPUProcesses()` または `CUDALibs()` のいずれか
  * `sequence::BlochSimulator`: カスタムシーケンス構造体
  * `parameters::SimulationParameters`: 各ボクセルのための異なる組織特性の組み合わせを含む配列。

# 注意

  * `resource == CUDALibs()` の場合、シーケンスとパラメータは、この関数を呼び出す前に `gpu(sequence)` と `gpu(parameters)` を使用してGPUに移動されている必要があります。
  * `resource == CPUProcesses()` の場合、パラメータは最初の次元がワーカーの数に対応する `DArray` である必要があります。この関数は、`DArray` の最初の次元に沿ってシミュレーションをワーカーに分配します。

# 戻り値

  * `magnetization::AbstractArray`: 入力組織特性のすべての組み合わせに対するシーケンスの磁化応答を含むサイズ (output_size(sequence), length(parameters)) の配列。
