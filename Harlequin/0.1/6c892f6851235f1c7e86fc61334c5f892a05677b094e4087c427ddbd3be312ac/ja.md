この構造体は、CMB静止フレームに対する太陽系の運動によって引き起こされるCMB双極子の温度の寄与を推定するために必要な情報をエンコードします。

# フィールド

  * `solsysdir_theta_rad`: 双極子軸のコラティチュード（ラジアン単位）
  * `solsysdir_phi_rad`: 双極子軸の経度（ラジアン単位）
  * `solsys_speed_m_s`: CMBに対する基準フレームの速度（m/s単位）
  * `solsys_velocity_m_s`: CMBに対する基準フレームの速度3ベクトル（m/s単位）
  * `tcmb_k`: CMBの熱力学的温度（ケルビン単位）

# オブジェクトの作成

`DipoleParameters`オブジェクトを作成する最も簡単な方法は、引数なしでコンストラクタを呼び出すことです。この場合、双極子軸はエクリプティック座標で提供され、Planck 2015による推定値が使用され、CMBモノポール温度の最良のCOBE推定値が使用されます。そうでない場合は、次のキーワードのいずれかを渡してパラメータを設定できます：

  * `theta_rad`は`SOLSYSDIR_ECL_THETA`がデフォルト
  * `phi_rad`は`SOLSYSDIR_ECL_PHI`がデフォルト
  * `speed_m_s`は`SOLSYSSPEED_M_S`がデフォルト
  * `t_k`は`T_CMB`がデフォルト

以下は、Planckの10%強い双極子を生成する例です：

```julia
using Harlequin # hide
dip = DipoleParameters(speed_m_s = SOLSYS_SPEED_VEC_M_S * 1.10)
```
