```julia
function correlationTest!(<same args and kwargs as `correlationTest`>)
```

[`correlationTest`](@ref) と同様ですが、`standardized` も `centered` も真でない場合、`x` は上書きされます。

*エイリアス:* `rTest!`, [`trendTest!`](@ref) 

*多重比較バージョン:* [correlationMcTest!](@ref)
