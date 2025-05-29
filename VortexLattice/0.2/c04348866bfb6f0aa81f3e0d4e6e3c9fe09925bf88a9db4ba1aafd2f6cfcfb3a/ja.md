```
generate_rotor(rotor_file::String, data_path="."; optargs...)
```

ローターファイルからグリッド、比率、セクション、法線の反転を生成します。ドキュメントで説明されています：

# 引数

  * `rotor_file`: ローターパラメータを含むファイル
  * `data_path`: rotor_fileフォルダーへのパス

# キーワード引数

  * `interpolate_airfoils_linear`: trueの場合、エアフォイルのポーラはエアフォイル間で線形に補間されます。デフォルトはfalseです。
  * `interpolate_airfoils_akima`: trueの場合、エアフォイルのポーラはエアフォイル間でアキマスプラインを使用して補間されます。
  * `zero_at_root`: trueの場合、エアフォイルの位置は根から定義され、そうでない場合はハブの中心から定義されます。デフォルトはfalseです。
  * `polar_in_radians`: trueの場合、エアフォイルのポーラはラジアンで、そうでない場合は度です。デフォルトはfalseです。
  * `turbine_flag`: trueの場合、ローターはタービンで、そうでない場合はプロペラです。デフォルトはfalseです。trueの場合、非線形ソルバーで迎角が反転します。
  * `clockwise`: trueの場合、ローターは時計回りに回転することを意図しており、そうでない場合は反時計回りです。デフォルトはfalseです。
  * `ns`: スパン方向のパネル数。デフォルトは10です。
  * `nc`: コード方向のパネル数。デフォルトは1です。
  * `spacing_s`: スパン方向の間隔。デフォルトは`VortexLattice.Sine()`です。
  * `spacing_c`: コード方向の間隔。デフォルトは`VortexLattice.Uniform()`です。
  * `initial_azimuthal_angle`: ローターの初期方位角。デフォルトは0.0です。
