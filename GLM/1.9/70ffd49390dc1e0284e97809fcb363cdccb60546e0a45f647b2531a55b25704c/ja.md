```
GLM.linkfun(L::Link, μ::Real)
```

リンク `L` における平均 `μ` の線形予測子の値 `η` を返します。

# 例

```jldoctest; setup = :(using GLM: linkfun, LogitLink)
julia> μ = inv(10):inv(5):1
0.1:0.2:0.9

julia> show(linkfun.(LogitLink(), μ))
[-2.197224577336219, -0.8472978603872036, 0.0, 0.8472978603872034, 2.1972245773362196]

```
