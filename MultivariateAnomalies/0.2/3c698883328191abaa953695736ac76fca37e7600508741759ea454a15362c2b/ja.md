```
init_KDE(K::Array{Float64, 2})
init_KDE(T::Int)
```

`KDE!()`で使用するための`KDE_out`オブジェクトを返します。引数としてカーネル行列`K`または時間ステップ/観測の数`T`のいずれかを使用します。
