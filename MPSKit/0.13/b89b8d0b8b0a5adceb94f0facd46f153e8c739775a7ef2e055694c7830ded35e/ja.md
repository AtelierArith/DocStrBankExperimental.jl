```
transferplot(above, below=above; sectors=[], transferkwargs=(;)[, kwargs...])
```

二つのInfiniteMPSの部分的な転送行列スペクトルをプロットします。

# 引数

  * `above::InfiniteMPS`: [`transfer_spectrum`](@ref)のための上のmps。
  * `below::InfiniteMPS=above`: [`transfer_spectrum`](@ref)のための下のmps。

# キーワード引数

  * `sectors=[]`: スペクトルを計算するためのセクターのベクトル。
  * `transferkwargs`: [`transfer_spectrum`](@ref)への呼び出しのためのkwargs。
  * `kwargs`: その他のkwargsはプロットバックエンドに渡されます。
  * `thetaorigin=0`: 角度範囲の起点。
  * `sector_formatter=string`: セクターを文字列に変換する方法。

!!! note
    この関数を使用するには、手動で[Plots.jl](https://github.com/JuliaPlots/Plots.jl)をインポートする必要があります。MPSKit.jlは[RecipesBase.jl](https://github.com/JuliaPlots/Plots.jl/tree/v2/RecipesBase)に基づいてプロットを定義していますが、ユーザーは実際にプロットを生成するために`using Plots`を追加する必要があります。

