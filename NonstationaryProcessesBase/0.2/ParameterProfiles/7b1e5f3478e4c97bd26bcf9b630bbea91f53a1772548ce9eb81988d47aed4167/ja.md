```
stepNoise()
```

白色雑音プロセスに従って、多くの四角い隆起と凹みの不連続関数を構成します。     'stepHeight':   ステップの高さの標準偏差     'T':            タプル、(t0, tmax)

# 例

```julia-repl
julia> D = stepNoise();
D([-1, 0, 1])
```
