```julia
irf(M, theta, beta, y)

```

アイテムパラメータ `beta` が与えられたとき、能力値 `theta` に対する応答 `y` のアイテム応答関数を評価します。

`y` が省略された場合、アイテム応答関数はすべての可能な応答に対して評価されます。

## 例

### 1パラメータロジスティックモデル

```jldoctest
julia> irf(OnePL, 0.0, 0.0, 1)
0.5

julia> irf(OnePL, 0.0, (; b = 0.5), 1)
0.37754066879814546

julia> irf(OnePL, 0.0, 0.5)
2-element Vector{Float64}:
 0.6224593312018545
 0.37754066879814546
```

### 2パラメータロジスティックモデル

```jldoctest
julia> beta = (a = 1.5, b = 0.5);

julia> irf(TwoPL, 0.0, beta, 1)
0.32082130082460697
```

### 3パラメータロジスティックモデル

```jldoctest
julia> beta = (a = 1.5, b = 0.5, c = 0.2);

julia> irf(ThreePL, 0.0, beta, 1)
0.4566570406596856
```

### 4パラメータロジスティックモデル

```jldoctest
julia> beta = (a = 1.5, b = 0.5, c = 0.2, d = 0.8);

julia> irf(FourPL, 0.0, beta, 1)
0.3924927804947642
```

### 部分クレジットモデル

```jldoctest
julia> beta = (b = -0.3, t = [-0.5, 1.3, -0.2]);

julia> irf(PCM, 0.0, beta)
4-element Vector{Float64}:
 0.09656592461423529
 0.07906149218108449
 0.3915941342939724
 0.4327784489107078

julia> irf(PCM, 0.0, beta, 3)
0.3915941342939724
```

### 一般化部分クレジットモデル

```jldoctest
julia> beta = (a = 1.3, b = 0.25, t = [0.0, 1.0]);

julia> irf(GPCM, 0.0, beta)
3-element Vector{Float64}:
 0.27487115408319557
 0.1986019275522736
 0.5265269183645309

julia> irf(GPCM, 0.0, beta, 1)
0.27487115408319557
```

### 評価スケールモデル

```jldoctest
julia> beta = (b = 0.0, t = zeros(2));

julia> irf(RSM, 0.0, beta)
3-element Vector{Float64}:
 0.3333333333333333
 0.3333333333333333
 0.3333333333333333

julia> irf(RSM, 0.0, beta, 3)
0.3333333333333333
```
