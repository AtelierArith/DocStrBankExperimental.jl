`FastBandlimited(s1, s2, fun, bandlimit;                 quadn_add=default_extra_quad(s1),                 roughpoints=nothing)`

`FastBandlimited`オブジェクトのコンストラクタで、行列`M`の作用を表します。`M[j,k] = g(s1[j] - s2[k])`であり、`g`は次の条件を満たします。

$ g(t) = ∫_{[-bandlimit, bandlimit]^{dim}} e^{-2 π i t^T ω} fun(ω) d ω $

ここで`t`と`Ω`はR^{dim}にあります。引数は次の通りです：

  * `s1::Union{Vector{Float64}, Vector{SVector{D,Float64}}` で `1 <= D <= 3`。
  * `s2::Union{Vector{Float64}, Vector{SVector{D,Float64}}` で `1 <= D <= 3`。
  * `bandlimit::Union{Float64, [iterable]{D,Float64}}`。複数の次元の点を渡す場合、`bandlimit`が`Float64`であれば、すべての次元で同じバンドリミットを意味します。

キーワード引数は次の通りです：

  * `quadn_add=default_extra_quad(s1)`。各次元でNyquistを超えて追加する数値積分ノードの数。1Dではこれを1000にしても問題ありませんが、3Dで1000にすると10^9ノードを追加することになります！注意してください。roughpointsを正しく提供すれば、この引数に触れる必要はないはずです。
  * `roughpoints::Union{Nothing, [iterable]{D,Float64}}=nothing`。この引数は、`fun`が滑らかでない場所を伝える方法です。これを行わないと、数値積分ルールの精度が大幅に低下します。このkwargは、あなたの位置の次元とタイプに一致する周波数の反復可能なものであるべきです。2D三角関数が原点で粗いことを`FastBandlimited`に伝える例として、fast sinc squared transformの例ファイルを参照してください。これは正しく設定することが重要な引数です！忘れた場合、コードがそれをキャッチする簡単な方法はなく、静かに間違った答えが返されるだけです。
