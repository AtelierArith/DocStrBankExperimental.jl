ModelingToolkit.jl PDESystemのドメイン情報。これは、初期条件や境界条件、座標変換をModelingToolkit.jl ODESystemまたはCatalyst.jl ReactionSystemに追加するために`+`演算子と共に使用できます。

**注意**: 独立変数（通常は時間）は、初期条件と境界条件のリストの最初に置く必要があります。

  * `partial_derivative_funcs`: 部分的独立変数の空間微分を返す関数で、オプションで最初に座標変換を行います。

    このパッケージの現在の関数オプションは次のとおりです：

      * `partialderivatives_δxyδlonlat`: `lat`および`lon`という名前の変数を度から直交メートルに変換した後、部分微分を返します。これは球状の地球を仮定しています。

    他のパッケージは追加の関数を実装することがあります。関数名は`partialderivatives_`で始めることが推奨されています。
  * `grid_spacing`: 部分的独立変数の離散化間隔。
  * `icbc`: 初期条件および/または境界条件のセット。
  * `spatial_ref`: ドメインの空間参照システム。
  * `time_offset`: ドメインの時間オフセット。
