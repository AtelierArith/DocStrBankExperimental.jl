ViscousFormulationBassiRebay1()

古典的なBR1フラックスは次のように定義されます。

  * F. Bassi, S. Rebay (1997) A High-Order Accurate Discontinuous Finite Element Method for the Numerical Solution of the Compressible Navier-Stokes Equations [DOI: 10.1006/jcph.1996.5572](https://doi.org/10.1006/jcph.1996.5572)

DGSEMに対するBR1スキームのより詳細な研究は次の文献にあります。

  * G. J. Gassner, A. R. Winters, F. J. Hindenlang, D. Kopriva (2018) The BR1 Scheme is Stable for the Compressible Navier-Stokes Equations [DOI: 10.1007/s10915-018-0702-1](https://doi.org/10.1007/s10915-018-0702-1)

BR1スキームは対流支配の問題に対してはうまく機能しますが、拡散支配の問題に対しては不安定性や収束の低下を引き起こす可能性があります。 後者の場合は、[`ViscousFormulationLocalDG`](@ref)スキームが推奨されます。
