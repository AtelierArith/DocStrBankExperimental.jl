```
rand(alg, dims::Tuple{Vararg{Int64,2}}; mask=nothing) where {T <: Integer}
```

`dims`（2つの整数のタプル）で定義されたモデルに従って、サイズのランドスケープを作成します。`mask`引数はブール値の行列を受け入れ、`nothing`でない場合は`mask!`に渡されます。
