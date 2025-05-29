```julia
expected_score(M, theta, betas; scoring_function)

```

アイテム応答モデル `M` の期待スコアを、アイテムパラメータのベクトル `betas` が与えられた能力値 `theta` で計算します。ベータの値は異なるアイテムのアイテムパラメータと見なされます。

期待スコアはモデルの [`irf`](@ref) 関数から計算されます。アイテムパラメータを [`irf`](@ref) に渡す方法の詳細については、各関数のドキュメントを参照してください。

## 応答スコアリング

期待スコアは、観測された応答パターン `x` の期待値として定義されます。したがって、任意の関数 `f(x)` の期待値も定義できます。応答を任意の値にマッピングする関数 `f` を `scoring_function` と呼びます。

## 例

### 1パラメータロジスティックモデル

```jldoctest
julia> betas = fill(0.0, 10);

julia> expected_score(OnePL, 0.0, betas)
5.0

julia> expected_score(OnePL, 0.0, betas; scoring_function = x -> 2x)
10.0
```

### 2パラメータロジスティックモデル

```jldoctest
julia> betas = fill((a = 1.5, b = 0.0), 5);

julia> expected_score(TwoPL, 0.0, betas)
2.5

julia> expected_score(TwoPL, 0.0, betas; scoring_function = x -> x + 1)
7.5
```

### 3パラメータロジスティックモデル

```jldoctest
julia> betas = fill((a = 0.4, b = 0.5, c = 0.1), 6);

julia> expected_score(ThreePL, 0.0, betas)
3.030896414512619
```

### 4パラメータロジスティックモデル

```jldoctest
julia> betas = fill((a = 1.4, b = 1.0, c = 0.15, d = 0.9), 7);

julia> expected_score(FourPL, 0.0, betas)
2.0885345850674453
```
