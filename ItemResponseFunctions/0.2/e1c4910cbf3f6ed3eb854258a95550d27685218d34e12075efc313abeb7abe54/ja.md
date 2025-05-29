```julia
iif(M, theta, beta, y)

```

アイテムパラメータ `beta` が与えられたとき、能力値 `theta` における応答 `y` のアイテム応答モデル `M` のアイテム情報関数を評価します。

`y` が省略されると、すべてのカテゴリのアイテムカテゴリ情報関数が返されます。

## 例

### 1パラメータロジスティックモデル

```jldoctest
julia> iif(OnePL, 0.0, 0.0, 1)
0.125

julia> iif(OnePL, 0.0, (; b = 0.0))
2-element Vector{Float64}:
 0.125
 0.125
```

### 2パラメータロジスティックモデル

```jldoctest
julia> iif(TwoPL, 0.0, (a = 1.3, b = 0.2))
2-element Vector{Float64}:
 0.2345721809921237
 0.1808672521393781
```

### 3パラメータロジスティックモデル

```jldoctest
julia> iif(ThreePL, 0.0, (a = 1.5, b = 0.5, c = 0.15))
2-element Vector{Float64}:
 0.2830301834782102
 0.033256997107963204
```

### 4パラメータロジスティックモデル

```jldoctest
julia> iif(FourPL, 0.0, (a = 2.1, b = -0.2, c = 0.15, d = 0.9))
2-element Vector{Float64}:
 0.1936328888005068
 0.3995140205278245
```
