@parallel*async kernelcall @parallel*async ∇=... kernelcall

!!! note "Advanced"
    ```
    @parallel_async ranges kernelcall
    @parallel_async nblocks nthreads kernelcall
    @parallel_async ranges nblocks nthreads kernelcall
    @parallel_async (...) configcall=... backendkwargs... kernelcall
    @parallel_async ∇=... ad_mode=... ad_annotations=... (...) backendkwargs... kernelcall
    ```


`kernelcall`を[`@parallel`](@ref)と同様に並列で宣言します（詳細は[`@parallel`](@ref)を参照）。ただし、呼び出しの最後で自動同期は無効になります。同期には[`@synchronize`](@ref)を使用してください。

!!! note "Performance note"
    現在、@parallel*asyncは、[`@init*parallel_stencil`](@ref)でThreadsまたはPolyesterパッケージが選択された場合、同期的に実行されるようにフォールバックします。


参照: [`@synchronize`](@ref), [`@parallel`](@ref)
