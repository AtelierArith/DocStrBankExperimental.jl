```
entanglementplot(state; site=0[, kwargs...])
```

与えられたMPS `state`の[エンタングルメントスペクトル](@ref entanglement_spectrum)をプロットします。

# 引数

  * `state`: エンタングルメントスペクトルを計算するためのMPS。

# キーワード引数

  * `site::Int=0`: マルチサイトユニットセルのためのMPSインデックス。スペクトルは`site`と`site + 1`の間の結合に対して計算されます。
  * `expand_symmetry::Logical=false`: 量子次元の重複を追加します。
  * `sortby=maximum`: セクターをソートする方法。
  * `sector_margin=1//10`: セクター間のホワイトスペースの量。
  * `sector_formatter=string`: セクターを文字列に変換する方法。
  * `kwargs...`: その他のキーワード引数はプロットバックエンドに渡されます。

!!! note
    この関数を使用するには、手動で[Plots.jl](https://github.com/JuliaPlots/Plots.jl)をインポートする必要があります。MPSKit.jlは[RecipesBase.jl](https://github.com/JuliaPlots/Plots.jl/tree/v2/RecipesBase)に基づいてプロットを定義していますが、ユーザーは実際にプロットを生成するために`using Plots`を追加する必要があります。

