```julia
struct SynapseParams{Tp}
```

Postsynaptic parameters.

---

# Units

  * time: ms
  * length: µm (area µm^2, volume µm^3)
  * voltage: mV
  * current: pA
  * conductance: nS
  * resistance: GOhm
  * capacitance: pF ( ms.pA/mV = ms.nS = ms/GOhm)
  * concentration: µM

---

# Fields

  * `LTP_region`: Region LTP Default: VPolygon([[6.35, 1.4], [10, 1.4], [6.35, 29.5], [10, 29.5]])
  * `LTD_region`: Region LTD Default: VPolygon([[6.35, 1.4], [6.35, 23.25], [6.35, 29.5], [1.85, 11.327205882352938], [1.85, 23.25], [3.7650354609929075, 1.4], [5.650675675675676, 29.5]])
  * `a_D`: **ACTIVATION RATES FOR THRESHOLDS** Default: 0.1
  * `b_D`: Default: 2.0e-5
  * `a_P`: Default: 0.2
  * `b_P`: Default: 0.0001
  * `t_D`: Default: 18000
  * `t_P`: Default: 13000
  * `K_D`: **Sigmoids controlling the rate of plasticity change** Default: 80000.0
  * `K_P`: Default: 13000.0
  * `rest_plstcty`: **Plasticity states** Default: 100
  * `t_end`: **SIMULATION** Default: 100
  * `sampling_rate`: Default: 10
  * `temp_rates`: **BIOPHYSICAL AND GHK PARAMETERS** Default: 35.0
  * `age`: Default: 60.0
  * `faraday`: Default: 0.096485 * 0.001
  * `Ca_ext`: Default: 2500.0
  * `Ca_infty`: Default: 0.05
  * `tau_ca`: Default: 10.0
  * `D_Ca`: Default: 0.3338
  * `f_Ca`: Default: 0.1
  * `perm`: Default: -0.04583333333333333
  * `z`: Default: 2.0
  * `gas`: Default: 8.314e-6
  * `p_release`: Default: (0.004225803293622208, 1708.4124496514878, 1.3499793762587964, 0.6540248201173222)
  * `trec`: **BACKPROPAGATION ATTENUATION** Default: 2000
  * `trec_soma`: Default: 500
  * `delta_decay`: Default: 1.7279e-5
  * `p_age_decay_bap`: Default: (0.13525468256031167, 16.482800452454164, 5.564691354645679)
  * `delta_soma`: Default: 2.5e-5 * (p*age*decay*bap[3] / (1 + exp(p*age*decay*bap[1] * (age - p*age*decay_bap[2]))))
  * `delta_aux`: Default: 2.304e-5
  * `injbap`: Default: 2.0
  * `soma_dist`: Default: 200.0
  * `p_dist`: Default: (0.019719018173341547, 230.3206470553394, 1.4313810030893268, 0.10406540965358434)
  * `ϕ_dist`: Default: p*dist[4] + p*dist[3] / (1 + exp(p*dist[1] * (soma*dist - p_dist[2])))
  * `I_clamp`: Default: 0.0
  * `gamma_Na`: **Na and K** Default: 800.0
  * `Erev_Na`: Default: 50.0
  * `gamma_K`: Default: 40.0
  * `Erev_K`: Default: -90.0
  * `p_nmda_frwd`: **NMDAr temperature modification** Default: (-0.09991802053299291, -37.63132907014948, 1239.0673283348326, -1230.6805720050966)
  * `frwd_T_chng_NMDA`: Default: p*nmda*frwd[4] + p*nmda*frwd[3] / (1 + exp(p*nmda*frwd[1] * (temp*rates - p*nmda_frwd[2])))
  * `p_nmda_bcwd`: Default: (-0.10605060141396823, 98.99939433046647, 1621.6168608608068, 3.0368551011554143)
  * `bcwd_T_chng_NMDA`: Default: p*nmda*bcwd[4] + p*nmda*bcwd[3] / (1 + exp(p*nmda*bcwd[1] * (temp*rates - p*nmda_bcwd[2])))
  * `NMDA_N2A_ka`: **NMDAr kinetics (GluN2A type)** Default: frwd*T*chng_NMDA * 34.0 * 0.001
  * `NMDA_N2A_kb`: Default: frwd*T*chng_NMDA * 17.0 * 0.001
  * `NMDA_N2A_kc`: Default: frwd*T*chng_NMDA * 127.0 * 0.001
  * `NMDA_N2A_kd`: Default: frwd*T*chng_NMDA * 580.0 * 0.001
  * `NMDA_N2A_ke`: Default: frwd*T*chng_NMDA * 2508.0 * 0.001
  * `NMDA_N2A_kf`: Default: frwd*T*chng_NMDA * 3449.0 * 0.001
  * `NMDA_N2A_k_f`: Default: bcwd*T*chng_NMDA * 662.0 * 0.001
  * `NMDA_N2A_k_e`: Default: bcwd*T*chng_NMDA * 2167.0 * 0.001
  * `NMDA_N2A_k_d`: Default: bcwd*T*chng_NMDA * 2610.0 * 0.001
  * `NMDA_N2A_k_c`: Default: bcwd*T*chng_NMDA * 161.0 * 0.001
  * `NMDA_N2A_k_b`: Default: bcwd*T*chng_NMDA * 120.0 * 0.001
  * `NMDA_N2A_k_a`: Default: bcwd*T*chng_NMDA * 60.0 * 0.001
  * `NMDA_N2B_sa`: **NMDAr kinetics (GluN2B type)** Default: frwd*T*chng_NMDA * 0.25 * 34.0 * 0.001
  * `NMDA_N2B_sb`: Default: frwd*T*chng_NMDA * 0.25 * 17.0 * 0.001
  * `NMDA_N2B_sc`: Default: frwd*T*chng_NMDA * 0.25 * 127.0 * 0.001
  * `NMDA_N2B_sd`: Default: frwd*T*chng_NMDA * 0.25 * 580.0 * 0.001
  * `NMDA_N2B_se`: Default: frwd*T*chng_NMDA * 0.25 * 2508.0 * 0.001
  * `NMDA_N2B_sf`: Default: frwd*T*chng_NMDA * 0.25 * 3449.0 * 0.001
  * `NMDA_N2B_s_f`: Default: bcwd*T*chng_NMDA * 0.23 * 662.0 * 0.001
  * `NMDA_N2B_s_e`: Default: bcwd*T*chng_NMDA * 0.23 * 2167.0 * 0.001
  * `NMDA_N2B_s_d`: Default: bcwd*T*chng_NMDA * 0.23 * 2610.0 * 0.001
  * `NMDA_N2B_s_c`: Default: bcwd*T*chng_NMDA * 0.23 * 161.0 * 0.001
  * `NMDA_N2B_s_b`: Default: bcwd*T*chng_NMDA * 0.23 * 120.0 * 0.001
  * `NMDA_N2B_s_a`: Default: bcwd*T*chng_NMDA * 0.23 * 60.0 * 0.001
  * `p_nmda`: Default: (0.004477162852447629, 2701.3929349701334, 58.38819453272428, 33.949463268365555)
  * `gamma_nmda`: Default: (p*nmda[4] + p*nmda[3] / (1 + exp(p*nmda[1] * (Ca*ext - p_nmda[2])))) * 0.001
  * `p_age`: Default: (0.09993657672916968, 25.102347872464193, 0.9642137892004939, 0.5075183905839776)
  * `r_NMDA_age`: **Ratio N2B/N2A** Default: rand(Normal(0, 0.05)) + p*age[4] + p*age[3] / (1 + exp(p*age[1] * (age - p*age[2])))
  * `N_NMDA`: Default: 15
  * `N_N2B`: Default: round((N*NMDA * r*NMDA*age) / (r*NMDA_age + 1))
  * `N_N2A`: Default: round(N*NMDA / (r*NMDA_age + 1))
  * `Erev_nmda`: **Other NMDAr parameters** Default: 0.0
  * `Mg`: Default: 1.0
  * `p_ampa_frwd`: **AMPAr temperature modification** Default: (-0.4737773089201679, 31.7248285571622, 10.273135485873242)
  * `frwd_T_chng_AMPA`: Default: p*ampa*frwd[3] / (1 + exp(p*ampa*frwd[1] * (temp*rates - p*ampa_frwd[2])))
  * `p_ampa_bcwd`: Default: (-0.36705555170278986, 28.976662403966674, 5.134547217640794)
  * `bcwd_T_chng_AMPA`: Default: p*ampa*bcwd[3] / (1 + exp(p*ampa*bcwd[1] * (temp*rates - p*ampa_bcwd[2])))
  * `AMPA_k1`: ** AMPAr kinetics  Default: frwd*T*chng_AMPA * 1.6 * 1.0e7 * 1.0e-6 * 0.001
  * `AMPA_k_1`: Default: bcwd*T*chng_AMPA * 7400 * 0.001
  * `AMPA_k_2`: Default: bcwd*T*chng_AMPA * 0.41 * 0.001
  * `AMPA_alpha`: Default: 2600 * 0.001
  * `AMPA_beta`: Default: 9600 * 0.001
  * `AMPA_delta_1`: Default: 1500 * 0.001
  * `AMPA_gamma_1`: Default: 9.1 * 0.001
  * `AMPA_delta_2`: Default: 170 * 0.001
  * `AMPA_gamma_2`: Default: 42 * 0.001
  * `AMPA_delta_0`: Default: 0.003 * 0.001
  * `AMPA_gamma_0`: Default: 0.83 * 0.001
  * `gamma_ampa1`: **AMPAr conductances** Default: 0.5 * 0.031
  * `gamma_ampa2`: Default: 0.5 * 0.052
  * `gamma_ampa3`: Default: 0.5 * 0.073
  * `N_ampa`: Default: 120
  * `Erev_ampa`: Default: 0.0
  * `N_GABA`: **GABAr** Default: 34
  * `p_Cl`: Default: (0.09151696057098718, 0.6919298240788684, 243.5159017060495, -92.6496083089155)
  * `Erev_Cl`: **GABAr, Cl reversal potential** Default: p*Cl[4] + p*Cl[3] / (1 + exp(p*Cl[1] * (age - p*Cl[2])))
  * `gamma_GABA`: Default: 0.035
  * `GABA_r_b1`: Default: 1.0e6 * 1.0e-6 * 0.001 * 20
  * `GABA_r_u1`: Default: 1000.0 * 0.0046
  * `GABA_r_b2`: Default: 1.0e6 * 1.0e-6 * 0.001 * 10
  * `GABA_r_u2`: Default: 1000.0 * 0.0092
  * `GABA_r_ro1`: Default: 1000.0 * 0.0033
  * `GABA_r_ro2`: Default: 1000.0 * 0.0106
  * `p_GABA`: Default: (0.19127068198185954, 32.16771140618756, -1.2798050197287802, 1.470692263981145)
  * `GABA_r_c1`: Default: (p*GABA[4] + p*GABA[3] / (1 + exp(p*GABA[1] * (temp*rates - p_GABA[2])))) * 1000.0 * 0.0098
  * `GABA_r_c2`: Default: (p*GABA[4] + p*GABA[3] / (1 + exp(p*GABA[1] * (temp*rates - p_GABA[2])))) * 0.4
  * `E_leak`: **Passive electrical properties** Default: -70.0
  * `g_leak`: Default: 4.0e-6
  * `Cm`: Default: 0.006
  * `R_a`: Default: 0.01
  * `D_dend`: ** MORPHOLOGY: Dendritic properties** Default: 2.0
  * `L_dend`: Default: 1400
  * `A_dend`: Default: 2 * pi * (D*dend / 2) * L*dend
  * `Vol_dend`: Default: pi * (D*dend / 2) ^ 2 * L*dend
  * `Cdend`: Default: Cm * A_dend
  * `CS_dend`: Default: pi * (D_dend / 2) .^ 2
  * `g_leakdend`: Default: g*leak * A*dend
  * `D_soma`: **MORPHOLOGY: Soma properties** Default: 30
  * `A_soma`: Default: pi * D_soma ^ 2
  * `Csoma`: Default: Cm * A_soma
  * `CS_soma`: Default: pi * (D_soma / 2) .^ 2
  * `g_leaksoma`: Default: 15.0
  * `g_diff`: Default: D*dend / (4R*a)
  * `Vol_sp`: **Spine properties** Default: 0.03
  * `A_sp`: Default: 4 * pi * ((3Vol_sp) / (4pi)) ^ (2.0 / 3.0)
  * `Csp`: Default: Cm * A_sp
  * `g_leaksp`: Default: g*leak * A*sp
  * `D_neck`: **Neck properties** Default: 0.1
  * `L_neck`: Default: 0.2
  * `CS_neck`: Default: pi * (D_neck / 2) .^ 2
  * `g_neck`: Default: CS*neck / (L*neck * R_a)
  * `tau_diff`: Default: Vol*sp / (2 * D*Ca * D*neck) + L*neck ^ 2 / (2D_Ca)
  * `glu_width`: **SYNAPTIC GLUTAMATE TRANSIENT PARAMETERS** Default: 1.0
  * `glu_amp`: Default: 1000.0
  * `glu_cv`: Default: 0.5
  * `N_SK`: **SK channels** Default: 15
  * `SK_gamma`: Default: 0.01
  * `SK_Erev`: Default: -90
  * `SK_gating_half`: Default: 0.33
  * `SK_time`: Default: 6.3
  * `SK_hill`: Default: 6
  * `p_SK_bcwd`: Default: (0.09391588258147192, 98.85165844770867, -147.61669527876904, 149.37767054612135)
  * `bcwd_SK`: Default: p*SK*bcwd[4] + p*SK*bcwd[3] / (1 + exp(p*SK*bcwd[1] * (temp*rates - p*SK_bcwd[2])))
  * `p_SK_frwd`: Default: (-0.334167923607112, 25.590920461511878, 2.2052151559841193, 0.005904170174699533)
  * `frwd_SK`: Default: p*SK*frwd[4] + p*SK*frwd[3] / (1 + exp(p*SK*frwd[1] * (temp*rates - p*SK_frwd[2])))
  * `CaM_con`: **Concentrations Default: 30.0
  * `mKCaM_con`: Default: 70.0
  * `mCaN_con`: Default: 20.0
  * `kon_1C`: **Chang Pepke model - CaM reactions I** Default: 0.005
  * `koff_1C`: Default: 0.05
  * `kon_2C`: Default: 0.01
  * `koff_2C`: Default: 0.01
  * `kon_1N`: Default: 0.1
  * `koff_1N`: Default: 2.0
  * `kon_2N`: Default: 0.2
  * `koff_2N`: Default: 0.5
  * `kf_CaM0`: **Chang Pepke model - CaM reactions II** Default: 3.8e-6
  * `kb_CaM0`: Default: 0.0055
  * `kf_CaM2C`: Default: 0.00092
  * `kb_CaM2C`: Default: 0.0068
  * `kf_CaM2N`: Default: 0.00012
  * `kb_CaM2N`: Default: 0.0017
  * `kf_CaM4`: Default: 0.03
  * `kb_CaM4`: Default: 0.0015
  * `kon_K1C`: **Chang Pepke model - CaMKII reactions** Default: 0.044
  * `koff_K1C`: Default: 0.033
  * `kon_K2C`: Default: 0.044
  * `koff_K2C`: Default: 0.0008
  * `kon_K1N`: Default: 0.076
  * `koff_K1N`: Default: 0.3
  * `kon_K2N`: Default: 0.076
  * `koff_K2N`: Default: 0.02
  * `p_camkii_q10`: **Chang Pepke model - autophosphorilation** Default: (0.5118207068695309, 45.47503600542303, -161.42634157226917, 162.1718925882677)
  * `q10`: Default: p*camkii*q10[4] + p*camkii*q10[3] / (1 + exp(p*camkii*q10[1] * (temp*rates - p*camkii_q10[2])))
  * `k1`: Default: 0.0126
  * `k2`: Default: q10 * 0.00033
  * `k3`: Default: 4 * q10 * 0.00017
  * `k4`: Default: 4 * 4.1e-5
  * `k5`: Default: 4 * q10 * 2 * 1.7e-5
  * `p_CaN_frwd`: **CaM-CaN reactions** Default: (-0.29481489145354556, 29.999999999999968, 0.15940019940354327, 0.870299900298228)
  * `kcanf`: Default: (p*CaN*frwd[4] + p*CaN*frwd[3] / (1 + exp(p*CaN*frwd[1] * (temp*rates - p*CaN_frwd[2])))) * 0.0175
  * `p_CaN_bcwd`: Default: (-0.6833299932488973, 26.277500129849113, 0.7114524682690591, 0.29037766196937326)
  * `kcanb`: Default: (p*CaN*bcwd[4] + p*CaN*bcwd[3] / (1 + exp(p*CaN*bcwd[1] * (temp*rates - p*CaN_bcwd[2])))) * 2.0e-5
  * `p_frwd_VGCC`: **VGCCs** Default: (1.0485098341579628, 30.66869198447378, -0.3040010721391852, 2.5032059559264357)
  * `frwd_VGCC`: Default: p*frwd*VGCC[4] + p*frwd*VGCC[3] / (1 + exp(p*frwd*VGCC[1] * (temp*rates - p*frwd_VGCC[2])))
  * `p_bcwd_VGCC`: Default: (-0.3302682317933842, 36.279019647221226, 3.2259761593440155, 0.7298285671937866)
  * `bcwd_VGCC`: Default: p*bcwd*VGCC[4] + p*bcwd*VGCC[3] / (1 + exp(p*bcwd*VGCC[1] * (temp*rates - p*bcwd_VGCC[2])))
  * `Erev_CaT`: Default: 10.0
  * `Erev_CaR`: Default: 10.0
  * `Erev_CaL`: Default: 10.0
  * `gamma_CaT`: Default: 0.012
  * `gamma_CaR`: Default: 0.017
  * `gamma_CaL`: Default: 0.027
  * `N_caT`: Default: 3
  * `N_caR`: Default: 3
  * `N_caL`: Default: 3
  * `EGTA_kf`: **Calcium dye and buffers** Default: 0.0027
  * `EGTA_kb`: Default: 0.18 * EGTA_kf
  * `EGTA_con`: Default: 0.0
  * `BAPTA_kf`: Default: 0.45
  * `BAPTA_kb`: Default: 0.176BAPTA_kf
  * `BAPTA_con`: Default: 0.0
  * `Imbuf_k_on`: Default: 0.247
  * `Imbuf_k_off`: Default: 0.524
  * `K_buff_diss`: Default: Imbuf*k*off / Imbuf*k*on
  * `Imbuf_con`: Default: 62
  * `Imbuf_con_dend`: Default: Imbuf_con * 4
  * `ogb1_kf`: **Calcium fluorescent dyes** Default: 0.8
  * `ogb1_kb`: Default: 0.16
  * `fluo4_kf`: Default: 0.8
  * `fluo4_kb`: Default: 0.24
  * `dye`: Default: 0.0
  * `fluo5f_kf`: Default: dye * 0.01
  * `fluo5f_kb`: Default: dye * 26 * fluo5f_kf
  * `fluo5f_con`: Default: dye * 200.0
