```
set_pair_coupling!(sys::System, op, bond)
```

任意の結合 `op` を `bond` に沿って設定します。この結合は、結晶対称性に従って同等の結合に伝播されます。これらの結合に対する以前の相互作用は上書きされます。パラメータ `bond` は `Bond(i, j, offset)` の形式を持ち、ここで `i` と `j` は単位セル内の原子インデックスであり、`offset` は単位セル内の変位です。演算子 `op` は、2つのスピン双極子演算子を受け入れる無名関数として提供することも、2つのサイトのテンソル積空間で作用する行列として提供することもできます。

# 例

```julia
# 3×3 行列 J1 と J2 を含む双線形+二次交換
set_pair_coupling!(sys, (Si, Sj) -> Si'*J1*Sj + (Si'*J2*Sj)^2, bond)

# 適切な固定行列表現を使用した同等の表現
S = spin_matrices(1/2)
Si, Sj = to_product_space(S, S)
set_pair_coupling!(sys, Si'*J1*Sj + (Si'*J2*Sj)^2, bond)
```

他の情報は [`spin_matrices`](@ref)、[`to_product_space`](@ref) を参照してください。
