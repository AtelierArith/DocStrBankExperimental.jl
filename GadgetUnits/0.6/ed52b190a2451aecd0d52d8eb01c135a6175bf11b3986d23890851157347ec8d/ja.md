```
GadgetPhysicalUnits(l_unit::T=3.085678e21, m_unit::T=1.989e43, v_unit::T=1.e5;
                    a_scale::T=1.0, hpar::T=1.0,
                    γ_th::T=5.0/3.0, xH::T=0.752) where T
```

構造体 `GadgetPhysicalUnits` を作成し、コモービングコード単位と物理単位の間の変換係数を保持します。Unitful または UnitfulAstro で変換可能な単位情報を格納します。

# キーワード引数

  * `a_scale::T = 1.0`:  シミュレーションの宇宙論的スケールファクター。ヘッダー `h` として `h.time` で渡すことができます。
  * `hpar::T = 1.0`:     '小さな h' としてのハッブル定数。ヘッダー `h` として `h.h0` で渡すことができます。
  * `γ_th::T = 5.0/3.0`: ガスの断熱指数。
  * `xH::T = 0.752`:      化学モデルなしで実行された場合のシミュレーションの水素比。

# フィールド

| 名前                        | 意味                            |
|:------------------------- |:----------------------------- |
| `x_cgs::Quantity{T}`      | cm 単位での位置                     |
| `x_physical::Quantity{T}` | kpc 単位での位置                    |
| `v_cgs::Quantity{T}`      | cm/s 単位での速度                   |
| `v_physical::Quantity{T}` | km/s 単位での速度                   |
| `m_cgs::Quantity{T}`      | g 単位での質量                      |
| `m_msun::Quantity{T}`     | 太陽質量単位での質量                    |
| `t_s::Quantity{T}`        | 秒単位での時間                       |
| `t_Myr::Quantity{T}`      | Myr 単位での時間                    |
| `E_cgs::Quantity{T}`      | erg 単位でのエネルギー                 |
| `E_eV::Quantity{T}`       | eV 単位でのエネルギー                  |
| `B_cgs::Quantity{T}`      | ガウス単位での磁場                     |
| `rho_cgs::Quantity{T}`    | $g/cm^3$ 単位での密度               |
| `rho_ncm3::Quantity{T}`   | $n_p/cm^3$ 単位での密度             |
| `T_K::Quantity{T}`        | K 単位での温度                      |
| `T_eV::Quantity{T}`       | eV 単位での温度                     |
| `P_th_cgs::Quantity{T}`   | Ba 単位での熱圧力                    |
| `P_CR_cgs::Quantity{T}`   | Ba 単位での宇宙線圧力                  |
| `CR_norm::Quantity{T}`    | cgs 単位での LMB*SPECTRAL*CRs ノルム |
