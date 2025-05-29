ComputationalResourcesは、異なる計算リソースを使用する異なるメソッドにディスパッチすることを可能にします。エクスポートされたリソースは次のとおりです：

  * `CPU1`（シングルスレッド計算）
  * `CPUThreads`（マルチスレッド計算）
  * `CPUProcesses`（マルチプロセス計算）
  * `ArrayFireLibs`（[ArrayFireパッケージ](https://github.com/JuliaComputing/ArrayFire.jl)を使用）
  * `CUDALibs`（NVIDIAのCUDAライブラリを使用したGPU計算）
  * `OpenCLLibs`（OpenCLライブラリを使用したGPU計算）

サポートされているメソッドの利用可能性を制御するために、パッケージ初期化機構と相互作用する関数もあります：

  * `addresource(T)`：新しくロードされたパッケージにリソース`T`をサポートするよう要求する
  * `rmresource(T)`：新しくロードされたパッケージにリソース`T`をサポートしないように要求するのを停止する
  * `haveresource(T)`：リソース`T`が要求されたかどうかをテストする
