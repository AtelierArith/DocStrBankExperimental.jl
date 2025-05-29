```
fftfreq(n, fs=1)
```

長さ `n` の離散フーリエ変換（DFT）サンプル周波数を返します。返される `Frequencies` オブジェクトは、各サンプルポイントでの周波数ビンの中心を含む `AbstractVector` です。`fs` は入力信号のサンプリングレートで、サンプル間隔の逆数です。

長さ `n` のウィンドウとサンプリングレート `fs` が与えられた場合、返される周波数は次のようになります。

```julia
[0:n÷2-1; -n÷2:-1]  * fs/n   # n が偶数の場合
[0:(n-1)÷2; -(n-1)÷2:-1]  * fs/n  # n が奇数の場合
```

# 例

```jldoctest; setup=:(using AbstractFFTs)
julia> fftfreq(4, 1)
4-element Frequencies{Float64}:
  0.0
  0.25
 -0.5
 -0.25

julia> fftfreq(5, 2)
5-element Frequencies{Float64}:
  0.0
  0.4
  0.8
 -0.8
 -0.4
```
