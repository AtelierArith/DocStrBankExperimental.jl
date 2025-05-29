```julia
trywait(sem) -> boolean
```

セマフォ `sem` を即座にデクリメント（ロック）し、成功した場合は `true` を返します。デクリメントが即座に実行できない場合、呼び出しは `false` を返します。中断が受信された場合や予期しないエラーが発生した場合は、例外がスローされます（それぞれ `InterruptException` または `SystemError`）。

参照: [`Semaphore`](@ref), [`post`](@ref), [`wait`](@ref),           [`timedwait`](@ref).
