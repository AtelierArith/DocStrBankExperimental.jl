```julia
post(sem)
```

はセマフォ `sem` をインクリメント（解除）します。セマフォの値が結果的にゼロより大きくなると、このセマフォで [`wait`](@ref) 呼び出し中にブロックされている別のプロセスまたはスレッドが起こされます。

関連情報: [`Semaphore`](@ref), [`wait`](@ref), [`timedwait`](@ref),           [`trywait`](@ref).
