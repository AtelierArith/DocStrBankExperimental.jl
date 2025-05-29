```julia
function goertzel_fast( x  :: AbstractVector{T},
                        wl :: Int,
                        a  :: Real,
                        c  :: Real,
                        s  :: Real,
                        d  :: Real,
                    startAT:: Int = 1) where T<:Union{Real, Complex}
```

関数が繰り返し呼び出され、速度が重要な場合は、[`goertzel`](@ref) 関数の高速バージョンを推奨します。ユーザーは以下の引数を提供します：

  * 入力ベクトル `x` としての時系列、
  * `wl`、`x` のサンプル数（またはウィンドウの長さ）、
  * `a` = $2/wl$、
  * `c` = $cos(p)$ ただし $p$=`2*π*round(UInt16, (f*wl)/sr)/wl`、$f$ は希望する周波数、$sr$ はサンプリングレート、
  * `s` = $sin(p)$
  * `d` = 2*`c`
  * [`goertzel`](@ref) 関数と同様に `startAt`。

**関連情報**: [`goertzel`](@ref), [`goertzel2`](@ref)。
