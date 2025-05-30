```julia
information(M, theta, betas; scoring_function)

```

アイテム応答モデル `M` のテスト情報を、能力値 `theta` とアイテムパラメータのベクトル `betas` を考慮して計算します。ベータの値は異なるアイテムのアイテムパラメータと見なされます。

テスト情報はモデル [`iif`](@ref) 関数から計算されます。アイテムパラメータを [`iif`](@ref) に渡す方法の詳細については、該当する関数のドキュメントを参照してください。

## 例

### 1パラメータロジスティックモデル

```jldoctest
julia> information(OnePL, 0.0, zeros(6))
1.5

julia> betas = fill((; b = 0.0), 6);

julia> information(OnePL, 0.0, betas)
1.5
```

### 2パラメータロジスティックモデル

```jldoctest
julia> betas = fill((; a = 1.2, b = 0.4), 4);

julia> information(TwoPL, 0.0, betas)
1.3601401228069936
```

### 3パラメータロジスティックモデル

```jldoctest
julia> betas = fill((; a = 1.5, b = 0.5, c = 0.2), 4);

julia> information(ThreePL, 0.0, betas)
1.1021806599852655
```

### 4パラメータロジスティックモデル

```jldoctest
julia> betas = fill((; a = 0.5, b = 1.4, c = 0.13, d = 0.94), 6);

julia> information(FourPL, 0.0, betas)
0.20178122985757524
```
