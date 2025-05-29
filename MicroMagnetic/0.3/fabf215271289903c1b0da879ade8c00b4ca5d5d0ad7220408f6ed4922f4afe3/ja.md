```
add_she_torque(sim::AbstractSim, sigma_s::Tuple{Real,Real,Real}, sigma_sa::Tuple{Real,Real,Real}; a1=(1,0,0), a2=(0,1,0), beta=0, name="she")
```

SHEトルクを表す効果的な場を追加します。

$$
\frac{\partial \mathbf{m}}{\partial t} = - \gamma \mathbf{m} \times \mathbf{H} + \alpha \mathbf{m} \times  \frac{\partial \mathbf{m}}{\partial t} 
- \mathbf{m} \times (\mathbf{m} \times \boldsymbol{\sigma}_{x y}^\mathrm{S H E}) -  \beta\mathbf{m} \times \boldsymbol{\sigma}_{x y}^\mathrm{S H E}
$$

同等の効果的な場は次のようになります。

$$
\mathbf{H}_\mathrm{she} = (1/\gamma)(\beta \boldsymbol{\sigma}_{x y}^\mathrm{S H E} + \mathbf{m} \times \boldsymbol{\sigma}_{x y}^\mathrm{S H E})
$$

ここで、

$$
\boldsymbol{\sigma}_{x y}^\mathrm{S H E}=\widetilde{\boldsymbol{\sigma}}_\mathrm{S} \times \hat{\mathbf{a}}_2-\left({\mathbf{m}} \cdot\left(\hat{\mathbf{a}}_2 \times \hat{\mathbf{a}}_1\right)\right)^2\left(\widetilde{\boldsymbol{\sigma}}_\mathrm{SA} \times \hat{\mathbf{a}}_2\right)
$$

### 例

```julia
    add_she_torque(sim, (0.1, 0.2, 0.3), (0.3, 0.4, 0.5), beta=0.1)
```
