```julia
person_parameter(M, responses, betas, alg; init, kwargs...)

```

アイテム応答理論モデル `M` に対して、アイテムパラメータ `beta` と推定アルゴリズム `alg` が与えられた応答ベクトル (`responses`) から単一の人物パラメータを推定します。

## 例

### 1パラメータロジスティックモデル

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> responses = [0, 1, 1, 0, 0];

julia> betas = [0.2, -1.3, 0.4, 1.2, 0.0];

julia> person_parameter(OnePL, responses, betas, MLE())
PersonParameter{Float64}(-0.34640709530672537, 0.9812365857368596)
```

### 3パラメータロジスティックモデル

```jldoctest; filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> responses = [0, 1, 1];

julia> betas = [(a = 1.0, b = 0.3, c = 0.1), (a = 0.3, b = -0.5, c = 0.0), (a = 1.4, b = 1.1, c = 0.3)];

julia> person_parameter(ThreePL, responses, betas, WLE())
PersonParameter{Float64}(0.657715606325967, 1.5321777539977457)
```
