```
SANDIdot(
    soma::Sphere 
    neurite::Stick
    extra::Iso 
    dot::Iso
    fracs::Vector{Float64} 
)
```

SANDIdotモデルには、SANDIモデルのためのドットコンパートメントが追加されています。ドットコンパートメントは不動の水と見なされ、ex vivoイメージングでより一般的に見られます。SANDIdotモデルでは、すべてのコンパートメントにおけるt2のフィールドを無視し、それらを0に設定します。フラクションベクターは、ソーマ、ニュライト、ドットのフラクションを表し、extraのフラクションは1-sum(fracs)となります。

# 参考文献

Alexander, D.C., Hubbard, P.L., Hall, M.G., Moore, E.A., Ptito, M., Parker, G.J.M., Dyrby, T.B., 2010. Orientationally invariant indices of axon diameter and density from diffusion MRI. Neuroimage 52, 1374–1389. https://doi.org/10.1016/j.neuroimage.2010.05.043

Panagiotaki, E., Schneider, T., Siow, B., Hall, M.G., Lythgoe, M.F., Alexander, D.C., 2012. Compartment models of the diffusion MR signal in brain white matter: A taxonomy and comparison. Neuroimage 59, 2241–2254. 

Palombo, M., Ianus, A., Guerreri, M., Nunes, D., Alexander, D.C., Shemesh, N., Zhang, H., 2020. SANDI: A compartment-based model for non-invasive apparent soma and neurite imaging by diffusion MRI. Neuroimage 215. https://doi.org/10.1016/j.neuroimage.2020.116835
