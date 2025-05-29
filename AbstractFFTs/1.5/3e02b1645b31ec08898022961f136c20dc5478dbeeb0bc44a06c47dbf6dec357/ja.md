```
rfftfreq(n, fs=1)
```

長さ `n` の実数 DFT の離散フーリエ変換 (DFT) サンプル周波数を返します。返される `Frequencies` オブジェクトは、各サンプルポイントでの周波数ビンの中心を含む `AbstractVector` です。`fs` は入力信号のサンプリングレートで、サンプル間隔の逆数です。

長さ `n` のウィンドウとサンプリングレート `fs` が与えられた場合、返される周波数は次のようになります。

```julia
[0:n÷2;]  * fs/n  # n が偶数の場合
[0:(n-1)÷2;]  * fs/n  # n が奇数の場合
```

!!! note
    ナイキスト周波数成分は正と見なされ、[`fftfreq`](@ref) とは異なります。


# 例

```jldoctest; setup=:(using AbstractFFTs)
julia> rfftfreq(4, 1)
3-element Frequencies{Float64}:
 0.0
 0.25
 0.5

julia> rfftfreq(5, 2)
3-element Frequencies{Float64}:
 0.0
 0.4
 0.8
```
