TaylorSpectral(param, index::NTuple{N}, freq0::Real, p0=zero(param))

周波数モデルを作成し、パラメータをテイラー級数で展開します。これは `param * exp(∑ₙ index[n] * log(Fr / freq0)^n)` + p0 で定義されます。すなわち、log(Fr / freq0) における展開であり、ここで Fr は観測の周波数、`freq0` は基準周波数、`param` は `freq0` でのパラメータ値です。オプションで、ゼロ次の項またはオフセットを定義する定数項 `p0` を展開に追加できます。

`index` の `N` はテイラー展開の次数を定義します。もし `index` が `<:Real` であれば、展開の次数は1です。
