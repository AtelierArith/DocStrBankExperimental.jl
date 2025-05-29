```
mapcols(f, m) ≈ mapreduce(f, hcat, eachcol(m)) ≈ mapslices(f, m, dims=1)
```

これは右側の関数のより効率的なバージョンです。`f(x::Vector)::Matrix`の場合、`mapslices(vec∘f, m, dims=1)`のように形状を変更します。`f(x::Vector)::Number`の場合は、削減をスキップし、単に`reshape(map(f, eachcol(m)),1,:)`を使用します。

これはTrackerとZygoteのための勾配を提供し、各スライスのための逆関数を保存します。

行列の後の任意の引数はスカラーとして`f`に渡されます。すなわち、`mapcols(f, m, args...) = reduce(hcat, f(col, args...) for col in eachcol(m))`です。これらはスライス/反復されず（`map`とは異なり）、その勾配も追跡されません。

`f`自体がパラメータを含む場合、それらの勾配も追跡されないことに注意してください。
