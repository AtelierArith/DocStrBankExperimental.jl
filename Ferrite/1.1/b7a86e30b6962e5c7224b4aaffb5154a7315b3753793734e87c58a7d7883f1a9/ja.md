```
ProjectedDirichlet(field_name::Symbol, facets::AbstractSet{FacetIndex}, f::Function; qr_order = -1)
```

`ProjectedDirichlet` 条件は、非ノード補間（例えば、$H(\mathrm{div})$ または $H(\mathrm{curl})$）の境界 `facets` における `field_name` の条件を強制し、関数 `f(x, t, n)` とファセット上の FE 近似によって記述される値 $\Gamma^f$ との間の L2 誤差を最小化します。関数への引数は、座標 $\boldsymbol{x}$、時間 $t$、およびファセット法線 $\boldsymbol{n}$ です。数値積分ルールは自動的に作成されますが、デフォルトの順序 `qr_order = 2 * ip_order`（将来のリリースで改良される可能性があります）は、必要に応じて上書きできます。

# H(div) 補間

H(div) の場合、法線フラックス $q_\mathrm{n} = f(\boldsymbol{x}, t, \boldsymbol{n})$ を指定したいと考えています。そのために、次の式を最小化するファセットに関連する自由度の値 $a_j^f$ を見つけたいと思います。

$$
U(\boldsymbol{q}(\boldsymbol{x})) = \int_{\Gamma^f}
\left[\boldsymbol{q}(\boldsymbol{x}) \cdot \boldsymbol{n} - f(\boldsymbol{x}, t, \boldsymbol{n}) \right]^2 \mathrm{d}\Gamma
$$

ここで、$\boldsymbol{q}(\boldsymbol{x}) = \boldsymbol{N}^f_j(\boldsymbol{x}) a_j^f$ です。すべての可能な方向 $\delta\boldsymbol{q}(\boldsymbol{x})$ に沿った方向微分を取ることで定常点を見つけると、

$$
0 = \lim_{\epsilon\rightarrow 0}\frac{\partial}{\partial \epsilon}
U\big(\boldsymbol{q}(\boldsymbol{x}) + \epsilon \delta\boldsymbol{q}(\boldsymbol{x})\big)
 = 2\int_{\Gamma^f} \left[\boldsymbol{q}(\boldsymbol{x}) \cdot \boldsymbol{n} - f(\boldsymbol{x}, t, \boldsymbol{n})\right]
    \delta\boldsymbol{q}(\boldsymbol{x}) \cdot \boldsymbol{n}\ \mathrm{d}\Gamma
$$

FE 近似 $\boldsymbol{q}(\boldsymbol{x}) = \boldsymbol{N}^f_j(\boldsymbol{x}) a_j^f$ および $\delta\boldsymbol{q}(\boldsymbol{x}) = \boldsymbol{N}^f_i(\boldsymbol{x}) c_i^f$ を挿入し、$c_i^f$ の任意性を使用すると、次の線形方程式系が得られます。

$$
\underbrace{\int_{\Gamma^f} \left[\delta\boldsymbol{N}^f_i \cdot \boldsymbol{n}^f\right]\left[\boldsymbol{N}^f_j \cdot \boldsymbol{n}^f\right]\ \mathrm{d}\Gamma}_{K^f_{ij}}\ a_j^f
= \underbrace{\int_{\Gamma^f} \left[\delta\boldsymbol{N}^f_i \cdot \boldsymbol{n}^f\right] f(\boldsymbol{x}, t, \boldsymbol{n})\ \mathrm{d}\Gamma}_{f^f_i}
$$

指定される係数 $a_j^f$ を決定します。

# H(curl) 補間

H(curl) の場合、接線フラックス $\boldsymbol{q}_\mathrm{t} = \boldsymbol{f}(\boldsymbol{x}, t, \boldsymbol{n})$ を指定したいと考えています。そのために、次の式を最小化するファセットに関連する自由度の値 $a_j^f$ を見つけたいと思います。

$$
U(\boldsymbol{q}(\boldsymbol{x})) = \int_{\Gamma^f}
\left\vert\left\vert
    \boldsymbol{q}(\boldsymbol{x}) \times \boldsymbol{n} - \boldsymbol{f}(\boldsymbol{x}, t, \boldsymbol{n})
\right\vert\right\vert^2
\mathrm{d}\Gamma
$$

ここで、$\boldsymbol{q}(\boldsymbol{x}) = \boldsymbol{N}^f_j(\boldsymbol{x}) a_j^f$ です。$H(\mathrm{div})$ と同様に、方向微分をゼロに設定することで最小値を見つけ、FE 近似を挿入すると次の線形方程式系が得られます。

$$
\underbrace{\int_{\Gamma^f} \left[\delta\boldsymbol{N}^f_i \times \boldsymbol{n}^f\right]\cdot\left[\boldsymbol{N}^f_j \times \boldsymbol{n}^f\right]\ \mathrm{d}\Gamma}_{K^f_{ij}}\ a_j^f
= \underbrace{\int_{\Gamma^f} \left[\delta\boldsymbol{N}^f_i \times \boldsymbol{n}^f\right]\cdot \boldsymbol{f}(\boldsymbol{x}, t, \boldsymbol{n})\ \mathrm{d}\Gamma}_{f^f_i}
$$

指定される係数 $a_j^f$ を決定します。 ```
