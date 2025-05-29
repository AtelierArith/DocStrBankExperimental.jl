```
convolution_range(m::Integral, M::Integral, n::Integer)
```

畳み込みの `m` 次の中央部分に対応する畳み込みベクトルのインデックスの範囲 `r` を計算します。ここで、`M` は畳み込みの最大次数、`N` は `M` 次の畳み込みに対応する畳み込みベクトルの長さ、`ℐ` は調和数です。

# 例

```julia-repl
julia> m = 1; M = 3; ℐ = 5; c_range = convolution_range(m, M, ℐ)
11:31
```
