```julia
sigpending() -> mask
```

は、呼び出しスレッドに配信待ちの信号のセットを返します（つまり、ブロック中に発生した信号）。返される値は[`SigSet`](@ref)のインスタンスです。

関連情報: [`sigpending!`](@ref).
