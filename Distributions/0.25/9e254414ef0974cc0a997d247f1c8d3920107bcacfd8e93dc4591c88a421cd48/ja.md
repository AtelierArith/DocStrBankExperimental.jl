```
MvLogNormal(d::MvNormal)
```

[多変量対数正規分布](http://en.wikipedia.org/wiki/Log-normal_distribution)は、*対数正規分布*の多次元一般化です。

もし $\boldsymbol X \sim \mathcal{N}(\boldsymbol\mu,\,\boldsymbol\Sigma)$ が多変量正規分布を持つならば、$\boldsymbol Y=\exp(\boldsymbol X)$ は多変量対数正規分布を持ちます。

基になる正規分布の平均ベクトル $\boldsymbol{\mu}$ と共分散行列 $\boldsymbol{\Sigma}$ は、対応する対数正規分布の*位置*および*スケール*パラメータとして知られています。
