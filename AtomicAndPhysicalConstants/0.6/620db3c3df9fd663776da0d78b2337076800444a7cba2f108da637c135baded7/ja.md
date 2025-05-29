SubatomicSpecies 

## 説明:

> ミュータブル構造体で、サブアトミック粒子に関するすべての（おそらく縮退した）情報を格納します<


## フィールド:

  * `species_name`      – （反）バリオンの一般的な名前の文字列
  * `charge`            – 与えられた粒子の電荷（単位は [e+]）
  * `mass`              – 与えられた粒子の質量（単位は [eV/c^2]）
  * `moment`  							– 粒子の磁気モーメント（単位は [eV/T]）
  * `spin`              – 粒子のスピン（単位は [ħ]）

## ノート:

この構造体のいくつかのパラメータは、PhysicalConstants.jl からの定数である可能性があります。

## 例:

  * `SubatomicSpecies("neutron", 0, m_neutron, anom_mag_moment_neutron, 0.5)`
  * `SubatomicSpecies("pion-", -1, m_pion_charged, 0.0, 0.0)`
