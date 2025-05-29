```
result::StatsBase.Histogram =
   bin_cmd(colors::AbstractVector{<:Number},
           mags::AbstractVector{<:Number};
           weights::AbstractVector{<:Number} = ones(promote_type(eltype(colors),
                                                    eltype(mags)), size(colors)),
           edges  = nothing,
           xlim   = extrema(colors),
           ylim   = extrema(mags),
           nbins  = nothing,
           xwidth = nothing,
           ywidth = nothing)
```

指定されたx軸の光度`colors`とy軸の光度マグニチュード`mags`からヘス図を含む`StatsBase.Histogram`型を返します。これらはすべて同じ長さのベクトルでなければなりません。`edges`キーワードを介してビンのエッジを直接指定することもできます（例：`edges = (range(-0.5, 1.6, length=100), range(17.0, 26.0, length=100))`）、または`xlim`と`ylim`を介してx軸とy軸の制限を設定し、`nbins`としてビンの数を指定することもできます。あるいは、`nbins`を省略し、代わりにx方向とy方向のビン幅である`xwidth`と`ywidth`を渡すこともできます。キーワード引数に関する詳細は以下を参照してください。これを`PyPlot.jl`でプロットするには、`PyPlot.imshow(permutedims(result.weights), origin="lower", extent=(extrema(result.edges[1])..., extrema(result.edges[2]), kws...)`を実行する必要があります。ここで、`kws...`は`PyPlot.imshow`に渡したい他のキーワード引数です。

# キーワード引数

  * `weights::AbstractVector{<:Number}`は、`colors`および`mags`と同じ長さの配列で、各点に関連付けられた確率的重みを含みます。これは`StatsBase.fit`に`StatsBase.Weights(weights)`として渡されます。以下のキーワード引数は、ヒストグラムのビンエッジを決定するために[`StarFormationHistories.calculate_edges`](@ref)に渡されます。
  * `edges`は、x軸（edges[1]）とy軸（edges[2]）に沿ったビンの左側エッジを定義する範囲のタプルです。例：`(-1.0:0.1:1.5, 22:0.1:27.2)`。`edges`が提供される場合、`weights`は唯一読み取られる他のキーワードです。`edges`は他の構築方法に優先します。
  * `xlim`は、提供された`colors`配列に対応するx軸の下限と上限を与える長さ2のインデックス可能なオブジェクト（例：ベクトルまたはタプル）です。例：`[-1.0, 1.5]`。これは`edges`が提供されていない場合にのみ使用されます。
  * `ylim`は、提供された`mags`配列に対応するy軸のための`xlim`のようなものです。例：`[25.0, 20.0]`。これは`edges`が提供されていない場合にのみ使用されます。
  * `nbins::NTuple{2, <:Integer}`は、x軸とy軸に沿って使用するビンの数を提供する整数の2タプルです。これは`edges`が提供されていない場合にのみ使用されます。
  * `xwidth`は、`colors`配列のx軸に沿ったビン幅です。これは`edges`と`nbins`が提供されていない場合にのみ使用されます。例：`0.1`。
  * `ywidth`は、提供された`mags`配列に対応するy軸のための`xwidth`のようなものです。例：`0.1`。
