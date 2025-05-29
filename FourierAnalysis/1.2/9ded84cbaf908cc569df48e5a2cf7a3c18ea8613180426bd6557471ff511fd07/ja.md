```julia
function goertzel( x   :: AbstractVector{T},
                   f   :: IntOrReal,
                   sr  :: Int,
                   wl  :: Int,
               startAT :: Int = 1) where T<:Union{Real, Complex}
```

入力ベクトル `x` として与えられた時間系列を `sr` サンプリングレートでサンプリングし、`f` に最も近い離散フーリエ周波数でのDFT複素係数を返します。この係数は、`startAt`（1ベース）から始まる時間ウィンドウの長さ `wl` に対して計算されます。

`startAT`=1（デフォルト）の場合、ベクトルの最初の `wl` サンプルが考慮されます。

`wl` は2の累乗である必要はありません。

**参照**: [`goertzel_fast`](@ref), [`goertzel2`](@ref).

**例**:

```julia
using FourierAnalysis
sr, t, f, a = 128, 128, 5, 10
v=sinusoidal(a, f, sr, t, 0)
c=goertzel(v, f, sr, t) # should output 0+aim
```
