Module ImplicitGlobalGrid

GPUおよびCPUアプリケーションのステンシルベースの分散並列化を、ほぼ自明に実現し、数千のGPU上での実世界のアプリケーションの理想的な弱スケーリングに近づけます。

# 一般的な概要と例

https://github.com/eth-cscs/ImplicitGlobalGrid.jl

# 関数

  * [`init_global_grid`](@ref)
  * [`finalize_global_grid`](@ref)
  * [`update_halo!`](@ref)
  * [`gather!`](@ref)
  * [`select_device`](@ref)
  * [`nx_g`](@ref)
  * [`ny_g`](@ref)
  * [`nz_g`](@ref)
  * [`x_g`](@ref)
  * [`y_g`](@ref)
  * [`z_g`](@ref)
  * [`tic`](@ref)
  * [`toc`](@ref)

関数の説明を表示するには、`?<functionname>`と入力してください。

!!! note "デバイスサポートの有効化"
    デバイスタイプ（CUDAまたはAMDGPU）のサポートは、ImplicitGlobalGridをインポートする前に対応するモジュール（CUDAまたはAMDGPU）をインポートすることで有効化されます（対応する拡張がロードされます）。


!!! note "パフォーマンスノート"
    システムがCUDA対応MPI（Nvidia GPU用）またはROCm対応MPI（AMD GPU用）をサポートしている場合、次の環境変数のいずれかを設定することでImplicitGlobalGridに対して有効化できます（遅くとも`init_global_grid`の呼び出し前に）：

    ```shell
    shell> export IGG_CUDAAWARE_MPI=1
    ```

    ```shell
    shell> export IGG_ROCMAWARE_MPI=1
    ```

