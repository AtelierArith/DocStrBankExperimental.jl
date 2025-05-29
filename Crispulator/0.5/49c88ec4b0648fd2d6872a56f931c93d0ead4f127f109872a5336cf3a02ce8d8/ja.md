```julia
select(setup, cells, cell_phenotypes, guides; debug)

```

`cells`は整数のベクトルで、`guides`はバーコードのベクトルです。与えられたカットオフを使用して、細胞を`bins`にシミュレートされたFACSソーティングを行います。`σ`はFACSスクリーニング中の表現型の広がりを指します。
