```julia
function goertzel2( x  :: AbstractVector{T},
                    f  :: IntOrReal,
                    sr :: Int,
                    wl :: Int,
                startAT:: Int = 1) where T<:Union{Real, Complex}
```

[`goertzel`](@ref) 関数と同様ですが、ナイキスト周波数までの全ての正の実数直線上でDFT係数を推定することを可能にします。これは、離散フーリエ周波数ではない周波数のDFT係数が求められる場合に便利です。

適切なテーパーを使用することで、この関数は1つの正弦波の場合において、全ての周波数で振幅と位相をほぼ正確に復元することができますが、`goertzel` 関数は正確なフーリエ離散周波数でのみそれを行うことができます。

**関連項目**: [`goertzel_fast`](@ref), [`goertzel`](@ref)。

**例**:

```julia
using FourierAnalysis
sr, t, f, a = 128, 128, 5, 10
ftrue=f+0.15
v=sinusoidal(a, ftrue, sr, t, 0 )
c=goertzel(v, f, sr, t) # 0+aim になるはずですが、明らかに失敗します
d=goertzel2(v, ftrue, sr, t) # こちらの方が近づきます
```
