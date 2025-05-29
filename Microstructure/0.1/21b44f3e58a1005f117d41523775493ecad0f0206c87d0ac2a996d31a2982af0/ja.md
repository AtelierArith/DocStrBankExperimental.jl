```
dMRI(nifti::MRI, 
tdelta::Vector{Float64}, 
dsmalldel::Vector{Float64}, 
techo::Vector{Float64}, 
smt::Bool,
nmeas::Vector{Int})
```

MRIオブジェクト`nifti`と、smt信号を特定するための追加のボリュームごとの実験設定`tdelta`、`tsmalldel`、`techo`、および測定の数を示す`nmeas`を持つdMRIタイプのオブジェクトを返します。
