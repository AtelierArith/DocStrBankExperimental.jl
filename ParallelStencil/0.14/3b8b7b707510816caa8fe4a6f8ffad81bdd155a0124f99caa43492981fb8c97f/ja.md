モジュール ParallelStencil

ドメイン科学者がGPUとCPUの両方で展開可能な高性能な並列ステンシル計算のための高レベルコードを書くことを可能にします。

# 一般的な概要と例

https://github.com/omlins/ParallelStencil.jl

# 主なマクロ

  * [`@init_parallel_stencil`](@ref)
  * [`@parallel`](@ref)
  * [`@hide_communication`](@ref)
  * [`@zeros`](@ref)
  * [`@ones`](@ref)
  * [`@rand`](@ref)
  * [`@falses`](@ref)
  * [`@trues`](@ref)
  * [`@fill`](@ref)
  * [`@fill!`](@ref)

!!! note "高度な"
      * [`@parallel_indices`](@ref)
      * [`@parallel_async`](@ref)
      * [`@synchronize`](@ref)


# [`@parallel_indices`](@ref) カーネル用のマクロ

  * [`@ps_show`](@ref)
  * [`@ps_println`](@ref)

!!! note "高度な"
      * [`@gridDim`](@ref)
      * [`@blockIdx`](@ref)
      * [`@blockDim`](@ref)
      * [`@threadIdx`](@ref)
      * [`@sync_threads`](@ref)
      * [`@sharedMem`](@ref)


# サブモジュール

  * [`ParallelStencil.AD`](@ref)
  * [`ParallelStencil.FieldAllocators`](@ref)
  * [`ParallelStencil.FiniteDifferences1D`](@ref)
  * [`ParallelStencil.FiniteDifferences2D`](@ref)
  * [`ParallelStencil.FiniteDifferences3D`](@ref)

# 呼び出し元で生成されるモジュール

  * [`Data`](@ref)

!! note "GPUサポートの有効化"     GPU（CUDA、AMDGPU、またはMetal）へのサポートは拡張機能で提供されており、したがって対応するパッケージ（CUDA.jl、AMDGPU.jl、またはMetal.jl）の明示的なインストールが必要です。対応するモジュール（CUDA、AMDGPU、またはMetal）を明示的にインポートする必要はありません。これは[`@init_parallel_stencil`](@ref)によって自動的に行われます。

マクロまたはモジュールの説明を表示するには、`?<macroname>`（`@`を含む）または`?<modulename>`と入力してください。
