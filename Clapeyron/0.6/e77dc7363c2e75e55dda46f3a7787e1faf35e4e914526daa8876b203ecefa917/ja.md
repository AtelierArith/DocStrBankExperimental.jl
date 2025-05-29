```
group_pairmean(groups::GroupParam,param::PairParam)
group_pairmean(f,groups::GroupParam,param::SingleParam)
```

`GroupParam` とパラメータ `P` を与えると、コンポーネントデータの単一パラメータ `p` を返します。ここで：

pᵢ = ∑νᵢₖ(∑(νᵢₗ*P(i,j))) / ∑νᵢₖ(∑νᵢₗ)

ここで `νᵢₖ` はコンポーネント `i` におけるグループ `k` の数であり、`P(i,j)` は `P` のタイプに依存します：

  * `P` が単一パラメータの場合、`P(i,j) = f(P[i],P[j])`
  * `P` がペアパラメータの場合、`P(i,j) = p[i,j]`
