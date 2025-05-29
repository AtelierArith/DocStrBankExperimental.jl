```
compute(::AbstractLimbDark, orbit::AbstractOrbit, t, r)
```

与えられた軌道から時刻 `t` におけるインパクトパラメータを計算することによって、相対フラックスを計算します。時刻は軌道の周期と互換性がある必要があり、通常は日単位です。

# 例

```jldoctest orb
julia> using Orbits

julia> ld = PolynomialLimbDark([0.4, 0.26]);

julia> orbit = SimpleOrbit(period=3, duration=1);

julia> ld(orbit, 0, 0.1) # プライマリイグレス
0.9878664434953113

julia> ld(orbit, 0.1, 0.1) # 0.1 d
0.9879670695533511
```

これは [Unitful.jl](https://github.com/painterqubits/Unitful.jl) のようなライブラリと共に問題なく動作します。

```jldoctest orb
julia> using Unitful

julia> orbit = SimpleOrbit(period=3u"d", duration=3u"hr");

julia> ld(orbit, 0u"d", 0.1)
0.9878664434953113
```
