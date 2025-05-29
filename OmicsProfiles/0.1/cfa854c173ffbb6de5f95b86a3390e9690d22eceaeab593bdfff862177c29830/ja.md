```
OmicsProfile(countmat, var, varindex; T=float(eltype(countmat)))
```

# 引数

  * `countmat`: 与えられたオミクスのカウント行列で、キー `:count` に設定されます。
  * `var::DataFrame`: 特徴または変数のメタ情報を含むデータフレーム。
  * `varindex::Symbol`: データフレーム `var` のインデックス。
  * `T`: `countmat` の要素型。

# 例

```jldoctest
julia> r, c = (100, 500)
(100, 500)

julia> data = rand(0:100, r, c);

julia> var = DataFrame(index=1:r, C=rand(r), D=rand(r));

julia> prof = OmicsProfile(data, var, :index)
OmicsProfile (nvar = 100):
    var: index, C, D
    layers: count
```
