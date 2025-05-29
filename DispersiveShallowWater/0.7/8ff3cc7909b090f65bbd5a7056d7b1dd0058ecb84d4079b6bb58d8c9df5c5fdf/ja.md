```
convergence_test([mod::Module=Main,] example::AbstractString, iterations; io::IO = stdout, kwargs...)
convergence_test([mod::Module=Main,] example::AbstractString, Ns::AbstractVector; io::IO = stdout, kwargs...)
```

`example`で与えられたセットアップを使用して複数のシミュレーションを実行し、$L^2$および$L^\infty$ノルムにおける実験的収束次数（EOC）を計算します。`iterations`が整数として渡された場合、各イテレーションでそれぞれのメッシュの解像度が2倍になります。`Ns`がベクトルとして渡された場合、シミュレーションは各`Ns`の値に対して実行されます。追加のキーワード引数`kwargs...`およびオプションのモジュール`mod`は、[`trixi_include`](@ref)に直接渡されます。

[Trixi.jl](https://github.com/trixi-framework/Trixi.jl)から調整されました。
