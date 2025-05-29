```julia
struct SynapseParams{Tp}
```

シナプス後パラメータ。

---

# 単位

  * 時間: ms
  * 長さ: µm (面積 µm^2, 体積 µm^3)
  * 電圧: mV
  * 電流: pA
  * コンダクタンス: nS
  * 抵抗: GOhm
  * 静電容量: pF ( ms.pA/mV = ms.nS = ms/GOhm)
  * 濃度: µM

---

# フィールド

  * `LTP_region`: LTP領域 デフォルト: VPolygon([[6.35, 1.4], [10, 1.4], [6.35, 29.5], [10, 29.5]])
  * `LTD_region`: LTD領域 デフォルト: VPolygon([[6.35, 1.4], [6.35, 23.25], [6.35, 29.5], [1.85, 11.327205882352938], [1.85, 23.25], [3.7650354609929075, 1.4], [5.650675675675676, 29.5]])
  * `a_D`: **閾値の活性化率** デフォルト: 0.1
  * `b_D`: デフォルト: 2.0e-5
  * `a_P`: デフォルト: 0.2
  * `b_P`: デフォルト: 0.0001
  * `t_D`: デフォルト: 18000
  * `t_P`: デフォルト: 13000
  * `K_D`: **可塑性変化の速度を制御するシグモイド** デフォルト: 80000.0
  * `K_P`: デフォルト: 13000.0
  * `rest_plstcty`: **可塑性状態** デフォルト: 100
  * `t_end`: **シミュレーション** デフォルト: 100
  * `sampling_rate`: デフォルト: 10
  * `temp_rates`: **生物物理学的およびGHKパラメータ** デフォルト: 35.0
  * `age`: デフォルト: 60.0
  * `faraday`: デフォルト: 0.096485 * 0.001
  * `Ca_ext`: デフォルト: 2500.0
  * `Ca_infty`: デフォルト: 0.05
  * `tau_ca`: デフォルト: 10.0
  * `D_Ca`: デフォルト: 0.3338
  * `f_Ca`: デフォルト: 0.1
  * `perm`: デフォルト: -0.04583333333333333
  * `z`: デフォルト: 2.0
  * `gas`: デフォルト: 8.314e-6
  * `p_release`: デフォルト: (0.004225803293622208, 1708.4124496514878, 1.3499793762587964, 0.6540248201173222)
  * `trec`: **逆伝播減衰** デフォルト: 2000
  * `trec_soma`: デフォルト: 500
  * `delta_decay`: デフォルト: 1.7279e-5
  * `p_age_decay_bap`: デフォルト: (0.13525468256031167, 16.482800452454164, 5.564691354645679)
  * `delta_soma`: デフォルト: 2.5e-5 * (p*age*decay*bap[3] / (1 + exp(p*age*decay*bap[1] * (age - p*age*decay_bap[2]))))
  * `delta_aux`: デフォルト: 2.304e-5
  * `injbap`: デフォルト: 2.0
  * `soma_dist`: デフォルト: 200.0
  * `p_dist`: デフォルト: (0.019719018173341547, 230.3206470553394, 1.4313810030893268, 0.10406540965358434)
  * `ϕ_dist`: デフォルト: p*dist[4] + p*dist[3] / (1 + exp(p*dist[1] * (soma*dist - p_dist[2])))
  * `I_clamp`: デフォルト: 0.0
  * `gamma_Na`: **NaおよびK** デフォルト: 800.0
  * `Erev_Na`: デフォルト: 50.0
  * `gamma_K`: デフォルト: 40.0
  * `Erev_K`: デフォルト: -90.0
  * `p_nmda_frwd`: **NMDAr温度修正** デフォルト: (-0.09991802053299291, -37.63132907014948, 1239.0673283348326, -1230.6805720050966)
  * `frwd_T_chng_NMDA`: デフォルト: p*nmda*frwd[4] + p*nmda*frwd[3] / (1 + exp(p*nmda*frwd[1] * (temp*rates - p*nmda_frwd[2])))
  * `p_nmda_bcwd`: デフォルト: (-0.10605060141396823, 98.99939433046647, 1621.6168608608068, 3.0368551011554143)
  * `bcwd_T_chng_NMDA`: デフォルト: p*nmda*bcwd[4] + p*nmda*bcwd[3] / (1 + exp(p*nmda*bcwd[1] * (temp*rates - p*nmda_bcwd[2])))
  * `NMDA_N2A_ka`: **NMDAr動力学（GluN2A型）** デフォルト: frwd*T*chng_NMDA * 34.0 * 0.001
  * `NMDA_N2A_kb`: デフォルト: frwd*T*chng_NMDA * 17.0 * 0.001
  * `NMDA_N2A_kc`: デフォルト: frwd*T*chng_NMDA * 127.0 * 0.001
  * `NMDA_N2A_kd`: デフォルト: frwd*T*chng_NMDA * 580.0 * 0.001
  * `NMDA_N2A_ke`: デフォルト: frwd*T*chng_NMDA * 2508.0 * 0.001
  * `NMDA_N2A_kf`: デフォルト: frwd*T*chng_NMDA * 3449.0 * 0.001
  * `NMDA_N2A_k_f`: デフォルト: bcwd*T*chng_NMDA * 662.0 * 0.001
  * `NMDA_N2A_k_e`: デフォルト: bcwd*T*chng_NMDA * 2167.0 * 0.001
  * `NMDA_N2A_k_d`: デフォルト: bcwd*T*chng_NMDA * 2610.0 * 0.001
  * `NMDA_N2A_k_c`: デフォルト: bcwd*T*chng_NMDA * 161.0 * 0.001
  * `NMDA_N2A_k_b`: デフォルト: bcwd*T*chng_NMDA * 120.0 * 0.001
  * `NMDA_N2A_k_a`: デフォルト: bcwd*T*chng_NMDA * 60.0 * 0.001
  * `NMDA_N2B_sa`: **NMDAr動力学（GluN2B型）** デフォルト: frwd*T*chng_NMDA * 0.25 * 34.0 * 0.001
  * `NMDA_N2B_sb`: デフォルト: frwd*T*chng_NMDA * 0.25 * 17.0 * 0.001
  * `NMDA_N2B_sc`: デフォルト: frwd*T*chng_NMDA * 0.25 * 127.0 * 0.001
  * `NMDA_N2B_sd`: デフォルト: frwd*T*chng_NMDA * 0.25 * 580.0 * 0.001
  * `NMDA_N2B_se`: デフォルト: frwd*T*chng_NMDA * 0.25 * 2508.0 * 0.001
  * `NMDA_N2B_sf`: デフォルト: frwd*T*chng_NMDA * 0.25 * 3449.0 * 0.001
  * `NMDA_N2B_s_f`: デフォルト: bcwd*T*chng_NMDA * 0.23 * 662.0 * 0.001
  * `NMDA_N2B_s_e`: デフォルト: bcwd*T*chng_NMDA * 0.23 * 2167.0 * 0.001
  * `NMDA_N2B_s_d`: デフォルト: bcwd*T*chng_NMDA * 0.23 * 2610.0 * 0.001
  * `NMDA_N2B_s_c`: デフォルト: bcwd*T*chng_NMDA * 0.23 * 161.0 * 0.001
  * `NMDA_N2B_s_b`: デフォルト: bcwd*T*chng_NMDA * 0.23 * 120.0 * 0.001
  * `NMDA_N2B_s_a`: デフォルト: bcwd*T*chng_NMDA * 0.23 * 60.0 * 0.001
  * `p_nmda`: デフォルト: (0.004477162852447629, 2701.3929349701334, 58.38819453272428, 33.949463268365555)
  * `gamma_nmda`: デフォルト: (p*nmda[4] + p*nmda[3] / (1 + exp(p*nmda[1] * (Ca*ext - p_nmda[2])))) * 0.001
  * `p_age`: デフォルト: (0.09993657672916968, 25.102347872464193, 0.9642137892004939, 0.5075183905839776)
  * `r_NMDA_age`: **N2B/N2A比** デフォルト: rand(Normal(0, 0.05)) + p*age[4] + p*age[3] / (1 + exp(p*age[1] * (age - p*age[2])))
  * `N_NMDA`: デフォルト: 15
  * `N_N2B`: デフォルト: round((N*NMDA * r*NMDA*age) / (r*NMDA_age + 1))
  * `N_N2A`: デフォルト: round(N*NMDA / (r*NMDA_age + 1))
  * `Erev_nmda`: **他のNMDArパラメータ** デフォルト: 0.0
  * `Mg`: デフォルト: 1.0
  * `p_ampa_frwd`: **AMPAr温度修正** デフォルト: (-0.4737773089201679, 31.7248285571622, 10.273135485873242)
  * `frwd_T_chng_AMPA`: デフォルト: p*ampa*frwd[3] / (1 + exp(p*ampa*frwd[1] * (temp*rates - p*ampa_frwd[2])))
  * `p_ampa_bcwd`: デフォルト: (-0.36705555170278986, 28.976662403966674, 5.134547217640794)
  * `bcwd_T_chng_AMPA`: デフォルト: p*ampa*bcwd[3] / (1 + exp(p*ampa*bcwd[1] * (temp*rates - p*ampa_bcwd[2])))
  * `AMPA_k1`: **AMPAr動力学 デフォルト: frwd*T*chng_AMPA * 1.6 * 1.0e7 * 1.0e-6 * 0.001
  * `AMPA_k_1`: デフォルト: bcwd*T*chng_AMPA * 7400 * 0.001
  * `AMPA_k_2`: デフォルト: bcwd*T*chng_AMPA * 0.41 * 0.001
  * `AMPA_alpha`: デフォルト: 2600 * 0.001
  * `AMPA_beta`: デフォルト: 9600 * 0.001
  * `AMPA_delta_1`: デフォルト: 1500 * 0.001
  * `AMPA_gamma_1`: デフォルト: 9.1 * 0.001
  * `AMPA_delta_2`: デフォルト: 170 * 0.001
  * `AMPA_gamma_2`: デフォルト: 42 * 0.001
  * `AMPA_delta_0`: デフォルト: 0.003 * 0.001
  * `AMPA_gamma_0`: デフォルト: 0.83 * 0.001
  * `gamma_ampa1`: **AMPArコンダクタンス** デフォルト: 0.5 * 0.031
  * `gamma_ampa2`: デフォルト: 0.5 * 0.052
  * `gamma_ampa3`: デフォルト: 0.5 * 0.073
  * `N_ampa`: デフォルト: 120
  * `Erev_ampa`: デフォルト: 0.0
  * `N_GABA`: **GABAr** デフォルト: 34
  * `p_Cl`: デフォルト: (0.09151696057098718, 0.6919298240788684, 243.5159017060495, -92.6496083089155)
  * `Erev_Cl`: **GABAr, Cl反転電位** デフォルト: p*Cl[4] + p*Cl[3] / (1 + exp(p*Cl[1] * (age - p*Cl[2])))
  * `gamma_GABA`: デフォルト: 0.035
  * `GABA_r_b1`: デフォルト: 1.0e6 * 1.0e-6 * 0.001 * 20
  * `GABA_r_u1`: デフォルト: 1000.0 * 0.0046
  * `GABA_r_b2`: デフォルト: 1.0e6 * 1.0e-6 * 0.001 * 10
  * `GABA_r_u2`: デフォルト: 1000.0 * 0.0092
  * `GABA_r_ro1`: デフォルト: 1000.0 * 0.0033
  * `GABA_r_ro2`: デフォルト: 1000.0 * 0.0106
  * `p_GABA`: デフォルト: (0.19127068198185954, 32.16771140618756, -1.2798050197287802, 1.470692263981145)
  * `GABA_r_c1`: デフォルト: (p*GABA[4] + p*GABA[3] / (1 + exp(p*GABA[1] * (temp*rates - p_GABA[2])))) * 1000.0 * 0.0098
  * `GABA_r_c2`: デフォルト: (p*GABA[4] + p*GABA[3] / (1 + exp(p*GABA[1] * (temp*rates - p_GABA[2])))) * 0.4
  * `E_leak`: **受動的電気特性** デフォルト: -70.0
  * `g_leak`: デフォルト: 4.0e-6
  * `Cm`: デフォルト: 0.006
  * `R_a`: デフォルト: 0.01
  * `D_dend`: **形態: 樹状突起の特性** デフォルト: 2.0
  * `L_dend`: デフォルト: 1400
  * `A_dend`: デフォルト: 2 * pi * (D*dend / 2) * L*dend
  * `Vol_dend`: デフォルト: pi * (D*dend / 2) ^ 2 * L*dend
  * `Cdend`: デフォルト: Cm * A_dend
  * `CS_dend`: デフォルト: pi * (D_dend / 2) .^ 2
  * `g_leakdend`: デフォルト: g*leak * A*dend
  * `D_soma`: **形態: 細胞体の特性** デフォルト: 30
  * `A_soma`: デフォルト: pi * D_soma ^ 2
  * `Csoma`: デフォルト: Cm * A_soma
  * `CS_soma`: デフォルト: pi * (D_soma / 2) .^ 2
  * `g_leaksoma`: デフォルト: 15.0
  * `g_diff`: デフォルト: D*dend / (4R*a)
  * `Vol_sp`: **スパインの特性** デフォルト: 0.03
  * `A_sp`: デフォルト: 4 * pi * ((3Vol_sp) / (4pi)) ^ (2.0 / 3.0)
  * `Csp`: デフォルト: Cm * A_sp
  * `g_leaksp`: デフォルト: g*leak * A*sp
  * `D_neck`: **ネックの特性** デフォルト: 0.1
  * `L_neck`: デフォルト: 0.2
  * `CS_neck`: デフォルト: pi * (D_neck / 2) .^ 2
  * `g_neck`: デフォルト: CS*neck / (L*neck * R_a)
  * `tau_diff`: デフォルト: Vol*sp / (2 * D*Ca * D*neck) + L*neck ^ 2 / (2D_Ca)
  * `glu_width`: **シナプスグルタミン酸過渡パラメータ** デフォルト: 1.0
  * `glu_amp`: デフォルト: 1000.0
  * `glu_cv`: デフォルト: 0.5
  * `N_SK`: **SKチャネル** デフォルト: 15
  * `SK_gamma`: デフォルト: 0.01
  * `SK_Erev`: デフォルト: -90
  * `SK_gating_half`: デフォルト: 0.33
  * `SK_time`: デフォルト: 6.3
  * `SK_hill`: デフォルト: 6
  * `p_SK_bcwd`: デフォルト: (0.09391588258147192, 98.85165844770867, -147.61669527876904, 149.37767054612135)
  * `bcwd_SK`: デフォルト: p*SK*bcwd[4] + p*SK*bcwd[3] / (1 + exp(p*SK*bcwd[1] * (temp*rates - p*SK_bcwd[2])))
  * `p_SK_frwd`: デフォルト: (-0.334167923607112, 25.590920461511878, 2.2052151559841193, 0.005904170174699533)
  * `frwd_SK`: デフォルト: p*SK*frwd[4] + p*SK*frwd[3] / (1 + exp(p*SK*frwd[1] * (temp*rates - p*SK_frwd[2])))
  * `CaM_con`: **濃度 デフォルト: 30.0
  * `mKCaM_con`: デフォルト: 70.0
  * `mCaN_con`: デフォルト: 20.0
  * `kon_1C`: **Chang Pepkeモデル - CaM反応 I** デフォルト: 0.005
  * `koff_1C`: デフォルト: 0.05
  * `kon_2C`: デフォルト: 0.01
  * `koff_2C`: デフォルト: 0.01
  * `kon_1N`: デフォルト: 0.1
  * `koff_1N`: デフォルト: 2.0
  * `kon_2N`: デフォルト: 0.2
  * `koff_2N`: デフォルト: 0.5
  * `kf_CaM0`: **Chang Pepkeモデル - CaM反応 II** デフォルト: 3.8e-6
  * `kb_CaM0`: デフォルト: 0.0055
  * `kf_CaM2C`: デフォルト: 0.00092
  * `kb_CaM2C`: デフォルト: 0.0068
  * `kf_CaM2N`: デフォルト: 0.00012
  * `kb_CaM2N`: デフォルト: 0.0017
  * `kf_CaM4`: デフォルト: 0.03
  * `kb_CaM4`: デフォルト: 0.0015
  * `kon_K1C`: **Chang Pepkeモデル - CaMKII反応** デフォルト: 0.044
  * `koff_K1C`: デフォルト: 0.033
  * `kon_K2C`: デフォルト: 0.044
  * `koff_K2C`: デフォルト: 0.0008
  * `kon_K1N`: デフォルト: 0.076
  * `koff_K1N`: デフォルト: 0.3
  * `kon_K2N`: デフォルト: 0.076
  * `koff_K2N`: デフォルト: 0.02
  * `p_camkii_q10`: **Chang Pepkeモデル - 自己リン酸化** デフォルト: (0.5118207068695309, 45.47503600542303, -161.42634157226917, 162.1718925882677)
  * `q10`: デフォルト: p*camkii*q10[4] + p*camkii*q10[3] / (1 + exp(p*camkii*q10[1] * (temp*rates - p*camkii_q10[2])))
  * `k1`: デフォルト: 0.0126
  * `k2`: デフォルト: q10 * 0.00033
  * `k3`: デフォルト: 4 * q10 * 0.00017
  * `k4`: デフォルト: 4 * 4.1e-5
  * `k5`: デフォルト: 4 * q10 * 2 * 1.7e-5
  * `p_CaN_frwd`: **CaM-CaN反応** デフォルト: (-0.29481489145354556, 29.999999999999968, 0.15940019940354327, 0.870299900298228)
  * `kcanf`: デフォルト: (p*CaN*frwd[4] + p*CaN*frwd[3] / (1 + exp(p*CaN*frwd[1] * (temp*rates - p*CaN_frwd[2])))) * 0.0175
  * `p_CaN_bcwd`: デフォルト: (-0.6833299932488973, 26.277500129849113, 0.7114524682690591, 0.29037766196937326)
  * `kcanb`: デフォルト: (p*CaN*bcwd[4] + p*CaN*bcwd[3] / (1 + exp(p*CaN*bcwd[1] * (temp*rates - p*CaN_bcwd[2])))) * 2.0e-5
  * `p_frwd_VGCC`: **VGCCs** デフォルト: (1.0485098341579628, 30.66869198447378, -0.3040010721391852, 2.5032059559264357)
  * `frwd_VGCC`: デフォルト: p*frwd*VGCC[4] + p*frwd*VGCC[3] / (1 + exp(p*frwd*VGCC[1] * (temp*rates - p*frwd_VGCC[2])))
  * `p_bcwd_VGCC`: デフォルト: (-0.3302682317933842, 36.279019647221226, 3.2259761593440155, 0.7298285671937866)
  * `bcwd_VGCC`: デフォルト: p*bcwd*VGCC[4] + p*bcwd*VGCC[3] / (1 + exp(p*bcwd*VGCC[1] * (temp*rates - p*bcwd_VGCC[2])))
  * `Erev_CaT`: デフォルト: 10.0
  * `Erev_CaR`: デフォルト: 10.0
  * `Erev_CaL`: デフォルト: 10.0
  * `gamma_CaT`: デフォルト: 0.012
  * `gamma_CaR`: デフォルト: 0.017
  * `gamma_CaL`: デフォルト: 0.027
  * `N_caT`: デフォルト: 3
  * `N_caR`: デフォルト: 3
  * `N_caL`: デフォルト: 3
  * `EGTA_kf`: **カルシウム染料およびバッファ** デフォルト: 0.0027
  * `EGTA_kb`: デフォルト: 0.18 * EGTA_kf
  * `EGTA_con`: デフォルト: 0.0
  * `BAPTA_kf`: デフォルト: 0.45
  * `BAPTA_kb`: デフォルト: 0.176BAPTA_kf
  * `BAPTA_con`: デフォルト: 0.0
  * `Imbuf_k_on`: デフォルト: 0.247
  * `Imbuf_k_off`: デフォルト: 0.524
  * `K_buff_diss`: デフォルト: Imbuf*k*off / Imbuf*k*on
  * `Imbuf_con`: デフォルト: 62
  * `Imbuf_con_dend`: デフォルト: Imbuf_con * 4
  * `ogb1_kf`: **カルシウム蛍光染料** デフォルト: 0.8
  * `ogb1_kb`: デフォルト: 0.16
  * `fluo4_kf`: デフォルト: 0.8
  * `fluo4_kb`: デフォルト: 0.24
  * `dye`: デフォルト: 0.0
  * `fluo5f_kf`: デフォルト: dye * 0.01
  * `fluo5f_kb`: デフォルト: dye * 26 * fluo5f_kf
  * `fluo5f_con`: デフォルト: dye * 200.0
