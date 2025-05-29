モジュール AD

Enzyme.jl パッケージの自動微分関数の GPU 互換ラッパーを提供します。ラップされた関数の使用方法については、Enzyme のドキュメントを参照してください。

# 使用法

```
import ParallelStencil.AD
```

# 関数

  * `autodiff_deferred!`: 関数 `autodiff_deferred` をラップし、Enzyme.Annotations でないすべての引数を Enzyme.Const に昇格させます。
  * `autodiff_deferred_thunk!`: 関数 `autodiff_deferred_thunk` をラップし、Enzyme.Annotations でないすべての引数を Enzyme.Const に昇格させます。

# 例

```
const USE_GPU = true
using ParallelStencil
import ParallelStencil.AD
using Enzyme
@static if USE_GPU
    @init_parallel_stencil(CUDA, Float64, 3);
else
    @init_parallel_stencil(Threads, Float64, 3);
end

@parallel_indices (ix) function f!(A, B, a)
    A[ix] += a * B[ix] * 100.65
    return
end

function main()
    N = 16
    a = 6.5
    A = @rand(N)
    B = @rand(N)
    Ā = @ones(size(A))
    B̄ = @ones(size(B))

    @info "running on CPU/GPU"
    @parallel f!(A, B, a) # f! の通常呼び出し
    @parallel configcall=f!(A, B, a) AD.autodiff_deferred!(Enzyme.Reverse, f!, Duplicated(A, Ā), DuplicatedNoNeed(B, B̄), Const(a)) # f! の自動微分
    
    return
end

main()
```

関数の説明を表示するには、`?<functionname>` と入力してください。
