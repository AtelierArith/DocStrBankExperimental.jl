```julia
person_parameters(M, responses, betas, alg)

```

アイテム応答理論モデルのタイプ `M` に対する人物パラメータを、アイテムパラメータ `betas`、推定アルゴリズム `alg`、および各人物の `responses` を考慮して推定します。

`responses` は、各エントリが1人の応答に対応する応答のベクトル、または `size(responses) == (n, length(betas))` の応答行列であることができます。すなわち、応答行列の各行は単一の人物の応答に対応します。

## 例

### 1パラメータロジスティックモデル

```jldoctest
julia> responses = [1 1 0; 0 1 0; 1 1 0; 0 0 1]
4×3 Matrix{Int64}:
 1  1  0
 0  1  0
 1  1  0
 0  0  1

julia> betas = [-0.1, 0.0, 1.0];

julia> person_parameters(OnePL, responses, betas, MLE());
```
