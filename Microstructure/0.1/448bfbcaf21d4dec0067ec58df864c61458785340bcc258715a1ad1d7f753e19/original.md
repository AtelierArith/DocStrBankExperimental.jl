```
compartment_signals(model::Compartment,protocol::Protocol)
```

Return compartment signals given a compartment object `model` and a imaging `protocol`.  `model` can be the `Cylinder`/`Zeppelin`/`Stick`/`Sphere`/`Iso` Type. When `t2` in compartment `model` is set as default (0),  relaxation-weightings are not considered in the signal equation.

### References

If you use these compartments to build models, please cite the recommended references. 

# For using any compartment in current release, please cite the following references for expressions of spherical mean/power averaging:

Callaghan, P.T., Jolley, K.W., Lelievre, J., 1979. Diffusion of water in the endosperm tissue of wheat grains as studied by pulsed field gradient nuclear magnetic resonance. Biophys J 28, 133. https://doi.org/10.1016/S0006-3495(79)85164-4

Kroenke, C.D., Ackerman, J.J.H., Yablonskiy, D.A., 2004. On the nature of the NAA diffusion attenuated MR signal in the central nervous system. Magn Reson Med 52, 1052–1059. https://doi.org/10.1002/MRM.20260

Kaden, E., Kruggel, F., Alexander, D.C., 2016. Quantitative mapping of the per-axon diffusion coefficients in brain white matter. Magn Reson Med 75, 1752–1763. https://doi.org/10.1002/MRM.25734

# Consider the following reference for overview of all tissue compartments:

Panagiotaki, E., Schneider, T., Siow, B., Hall, M.G., Lythgoe, M.F., Alexander, D.C., 2012. Compartment models of the diffusion MR signal in brain white matter: A taxonomy and comparison. Neuroimage 59, 2241–2254. 

# Cylinder compartment:

Van Gelderen, P., Des Pres, D., Van Zijl, P.C.M., Moonen, C.T.W., 1994. Evaluation of Restricted Diffusion in Cylinders. Phosphocreatine in Rabbit Leg Muscle. J Magn Reson B 103, 255–260. https://doi.org/10.1006/JMRB.1994.1038

Alexander, D.C., Hubbard, P.L., Hall, M.G., Moore, E.A., Ptito, M., Parker, G.J.M., Dyrby, T.B., 2010. Orientationally invariant indices of axon diameter and density from diffusion MRI. Neuroimage 52, 1374–1389. https://doi.org/10.1016/j.neuroimage.2010.05.043

Fan, Q., Nummenmaa, A., Witzel, T., Ohringer, N., Tian, Q., Setsompop, K., Klawiter, E.C., Rosen, B.R., Wald, L.L., Huang, S.Y., 2020. Axon diameter index estimation independent of fiber orientation distribution using high-gradient diffusion MRI. Neuroimage 222. 

Andersson, M., Pizzolato, M., Kjer, H.M., Skodborg, K.F., Lundell, H., Dyrby, T.B., 2022. Does powder averaging remove dispersion bias in diffusion MRI diameter estimates within real 3D axonal architectures? Neuroimage 248. 

# Sphere compartment:

Neuman, C.H., 1974. Spin echo of spins diffusing in a bounded medium. J Chem Phys 4508–4511. https://doi.org/10.1063/1.1680931

Balinov, B., Jönsson, B., Linse, P., Söderman, O., 1993. The NMR Self-Diffusion Method Applied to Restricted Diffusion. Simulation of Echo Attenuation from Molecules in Spheres and between Planes. J Magn Reson A 104, 17–25. https://doi.org/10.1006/JMRA.1993.1184

# Stick compartment:

Behrens, T.E.J., Woolrich, M.W., Jenkinson, M., Johansen-Berg, H., Nunes, R.G., Clare, S., Matthews, P.M., Brady, J.M., Smith, S.M., 2003. Characterization and Propagation of Uncertainty in Diffusion-Weighted MR Imaging. Magn Reson Med 50, 1077–1088. https://doi.org/10.1002/MRM.10609

Panagiotaki, E., Schneider, T., Siow, B., Hall, M.G., Lythgoe, M.F., Alexander, D.C., 2012. Compartment models of the diffusion MR signal in brain white matter: A taxonomy and comparison. Neuroimage 59, 2241–2254. 

Zhang, H., Schneider, T., Wheeler-Kingshott, C.A., Alexander, D.C., 2012. NODDI: Practical in vivo neurite orientation dispersion and density imaging of the human brain. Neuroimage 61, 1000–1016. https://doi.org/10.1016/j.neuroimage.2012.03.072

# Zeppelin & Iso:

Alexander, D.C., 2008. A General Framework for Experiment Design in Diffusion MRI and Its Application in Measuring Direct Tissue-Microstructure Features. Magn Reson Med 60, 439–448. https://doi.org/10.1002/mrm.21646

Panagiotaki, E., Schneider, T., Siow, B., Hall, M.G., Lythgoe, M.F., Alexander, D.C., 2012. Compartment models of the diffusion MR signal in brain white matter: A taxonomy and comparison. Neuroimage 59, 2241–2254. 

Zhang, H., Schneider, T., Wheeler-Kingshott, C.A., Alexander, D.C., 2012. NODDI: Practical in vivo neurite orientation dispersion and density imaging of the human brain. Neuroimage 61, 1000–1016. https://doi.org/10.1016/j.neuroimage.2012.03.072

# Compartmental T2-weighting:

Veraart, J., Novikov, D.S., Fieremans, E., 2017. TE dependent Diffusion Imaging (TEdDI) distinguishes between compartmental T 2 relaxation times. https://doi.org/10.1016/j.neuroimage.2017.09.030

Lampinen, B., Szczepankiewicz, F., Novén, M., van Westen, D., Hansson, O., Englund, E., Mårtensson, J., Westin, C.F., Nilsson, M., 2019. Searching for the neurite density with diffusion MRI: Challenges for biophysical modeling. Hum Brain Mapp 40, 2529–2545. https://doi.org/10.1002/hbm.24542

Gong, T., Tong, Q., He, H., Sun, Y., Zhong, J., Zhang, H., 2020. MTE-NODDI: Multi-TE NODDI for disentangling non-T2-weighted signal fractions from compartment-specific T2 relaxation times. Neuroimage 217. https://doi.org/10.1016/j.neuroimage.2020.116906

Gong, T., Tax, C.M., Mancini, M., Jones, D.K., Zhang, H., Palombo, M., 2023. Multi-TE SANDI: Quantifying compartmental T2 relaxation times in the grey matter. Toronto.
