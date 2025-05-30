```
heideldiag(
    x::AbstractVector{<:Real}; alpha::Real=0.05, eps::Real=0.1, start::Int=1, kwargs...
)
```

HeidelbergerおよびWelch診断を計算します[^Heidelberger1983]。この診断は、非収束（非定常性）および推定区間の半幅と平均の比率が目標比率内にあるかどうかをテストします。定常性は、有意なテストp値の場合に拒否されます（0）。観測された比率が目標を超える場合、半幅テストは拒否されます（0）。これは`s2`および`beta[1]`の場合です。

`kwargs`は[`mcse`](@ref)に転送されます。

[^Heidelberger1983]: Heidelberger, P., & Welch, P. D. (1983). Simulation run length control in the presence of an initial transient. Operations Research, 31(6), 1109-1144.
