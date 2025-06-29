```
suggest_magnetic_supercell(ks; tol=1e-12, maxsize=100)
```

波ベクトル `ks` の周期性と一致する結晶格子ベクトルの単位で、磁気スーパーセルを提案します。波ベクトルが最大スーパーセルサイズ `maxsize` に対して不整合な場合、より大きな誤差許容値 `tol` を選択して、ほぼ整合するスーパーセルを見つけることができます。

[`reshape_supercell`](@ref) で使用するのに適した整数の $3×3$ 行列を出力します。

# 例

```julia
# 単一-Q 構造のための磁気スーパーセル。出力されます
k1 = [0, -1/4, 1/4]
suggest_magnetic_supercell([k1])       # [1 0 0; 0 2 1; 0 -2 1]

# ダブル-Q 構造のためのより大きな磁気スーパーセル
k2 = [1/4, 0, 1/4]
suggest_magnetic_supercell([k1, k2])   # [1 2 2; -1 2 -2; -1 2 2]

# 不整合な波ベクトルが与えられた場合、近くの波ベクトルに対して
# 正確に整合する近似スーパーセルを見つけます。
suggest_magnetic_supercell([[0, 0, 1/√5], [0, 0, 1/√7]]; tol=1e-2)

# これは [1 0 0; 0 1 0; 0 0 16] を出力し、近似 `1/√5 ≈ 7/16` と
# `1/√7 ≈ 3/8` の下で整合します。
```
