```
MatrixBeta(p, n1, n2)
```

```julia
p::Int    次元
n1::Real  自由度 (p - 1 より大きい)
n2::Real  自由度 (p - 1 より大きい)
```

[マトリックスベータ分布](https://en.wikipedia.org/wiki/Matrix_variate_beta_distribution)は、$\mathbf{U}$という$p\times p$の実行列に対してベータ分布を一般化したもので、$\mathbf{U}$と$\mathbf{I}_p-\mathbf{U}$の両方が正定値である必要があります。もし$\mathbf{U}\sim \textrm{MB}_p(n_1/2, n_2/2)$であれば、その確率密度関数は次のようになります。

$$
f(\mathbf{U}; n_1,n_2) = \frac{\Gamma_p(\frac{n_1+n_2}{2})}{\Gamma_p(\frac{n_1}{2})\Gamma_p(\frac{n_2}{2})}
|\mathbf{U}|^{(n_1-p-1)/2}\left|\mathbf{I}_p-\mathbf{U}\right|^{(n_2-p-1)/2}.
$$

もし$\mathbf{S}_1\sim \textrm{W}_p(n_1,\mathbf{I}_p)$および$\mathbf{S}_2\sim \textrm{W}_p(n_2,\mathbf{I}_p)$が独立であり、$\mathcal{L}(\cdot)$を下Cholesky因子を示す記号とすると、

$$
\mathbf{U}=\mathcal{L}(\mathbf{S}_1+\mathbf{S}_2)^{-1}\mathbf{S}_1\mathcal{L}(\mathbf{S}_1+\mathbf{S}_2)^{-\rm{T}}
$$

は$\mathbf{U}\sim \textrm{MB}_p(n_1/2, n_2/2)$となります。
