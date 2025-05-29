ChabocheThermal材料の問題状態。

  * `stress`: 応力テンソル
  * `R`: 降伏強度（等方硬化）
  * `X1`: バックストレス1（運動硬化）
  * `X2`: バックストレス2（運動硬化）
  * `X3`: バックストレス3（運動硬化）
  * `plastic_strain`: 応力テンソルの塑性部分
  * `cumeq`: 累積等価塑性ひずみ（スカラー, ≥ 0）
  * `jacobian`: ∂σij/∂εkl（アルゴリズミック）

他の `dXXXdYYY` プロパティは、指定された変数のアルゴリズミックヤコビアンです。

ひずみテンソルへの弾性および熱的寄与は保存されません。それらを取得するには：

```
θ₀ = ...
θ = ...
p = material.parameters
v = material.variables

C(θ) = compliance_tensor(p.E, p.nu, θ)
elastic_strain = dcontract(C(θ), v.stress)

thermal_strain = thermal_strain_tensor(p.alpha, θ₀, θ)
```

次のようになります：

```
material.drivers.strain = elastic_strain + v.plastic_strain + thermal_strain
```
