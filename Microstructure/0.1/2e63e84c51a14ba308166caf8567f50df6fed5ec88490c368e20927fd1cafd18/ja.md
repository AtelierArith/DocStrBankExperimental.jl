```
SANDI(
    soma::Sphere,
    neurite::Stick,
    extra::Iso,
    fracs::Vector{Float64}
    )
```

細胞体および神経突起密度イメージング（SANDI）モデルは、細胞体をモデル化するための球体コンパートメント、神経突起をモデル化するためのスティックコンパートメント、細胞外空間のための等方性拡散コンパートメントを使用します。各コンパートメントにはすべての組織パラメータが含まれ、`fracs`ベクトルは細胞体内信号および神経突起内信号の割合を表します（細胞外信号の割合は1-sum(fracs)です）。SANDIモデルでは、すべてのコンパートメントの`t2`フィールドを無視し、0に設定します。

# 参考文献

Palombo, M., Ianus, A., Guerreri, M., Nunes, D., Alexander, D.C., Shemesh, N., Zhang, H., 2020. SANDI: A compartment-based model for non-invasive apparent soma and neurite imaging by diffusion MRI. Neuroimage 215. https://doi.org/10.1016/j.neuroimage.2020.116835
