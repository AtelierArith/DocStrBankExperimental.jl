```
convergence_test([mod::Module=Main,] elixir::AbstractString, iterations, RealT = Float64; kwargs...)
```

`elixir`で与えられたセットアップを使用して`iterations`回のTrixi.jlシミュレーションを実行し、$L^2$および$L^\infty$ノルムにおける実験的収束次数（EOC）を計算します。`RealT`をエラーを表すデータ型として使用します。各イテレーションでは、対応するメッシュの解像度が2倍になります。追加のキーワード引数`kwargs...`とオプションのモジュール`mod`は、[`trixi_include`](@ref)に直接渡されます。

この関数は、空間解像度がキーワード`initial_refinement_level`（整数）または`cells_per_dimension`（空間次元ごとに1つの整数のタプル）を介して設定されていると仮定します。
