STMM実行のための設定。

  * `working_directory`: 中間結果を保存するフォルダー。デフォルトは`""`で、これは現在のディレクトリ内に一時フォルダーが作成され、作業ディレクトリとして使用されることを意味します。
  * `number_processors`: 開始するプロセスの数。デフォルトは`1`。
  * `output_file`: 出力ファイルの名前。デフォルトは`"mstm.out"`。
  * `run_print_file`: 実行情報を保存するファイルの名前。デフォルトは`"mstm.run"`。
  * `target_euler_angles_deg`: [**MSTM v3**] 指定されたオイラー角を使用してターゲット座標系の周りにターゲットを回転させます。デフォルトは`(0.0, 0.0, 0.0)`。
  * `mie_epsilon`: [**MSTM v3**, **MSTM v4**] 各球の波動関数展開の切断次数を決定するための収束基準。デフォルトは`1e-6`。

    > すべての球の展開を`L`-次で切断するように強制するために、負の整数`-L`として設定することもできます。
  * `translation_epsilon`: [**MSTM v3**, **MSTM v4**] クラスターのT行列の最大次数を推定するための収束基準。デフォルトは`1e-6`。
  * `solution_epsilon`: [**MSTM v3**, **MSTM v4**, **FaSTMM**] 反復ソルバーの誤差基準（**MSTM**のための双共役勾配法、**FaSTMM**のためのGMRES）。デフォルトは`1e-8`。
  * `max_t_matrix_order`: [**MSTM v4**] T行列の最大切断次数。これは、主にメモリ割り当て制限によるコードのクラッシュを防ぐために必要です。デフォルトは`120`。
  * `t_matrix_epsilon`: [**MSTM v3**] T行列解の収束基準。デフォルトは`1e-7`。

    > MSTM v4もこのオプションをサポートするはずですが、まだ実装されていません。
  * `max_iterations`: [**MSTM v3**, **MSTM v4**, **FaSTMM**] 解に到達するために試みる最大反復回数。デフォルトは`5000`。
  * `store_translation_matrix`: [**MSTM v3**, **MSTM v4**] `= false`の場合、近接場の変換行列は反復中に計算され、メモリに保存されません；`= true`の場合、近接場の行列は解の前に計算され、メモリに保存されます。メモリに行列を保存すると実行時間が改善されますが、使用されるメモリ量と利用可能なリソースはチェックされません。このオプションは自己責任で使用してください。デフォルトは`false`。
  * `sm_number_processors`: [**MSTM v3**] ランダム方向散乱行列の展開係数を計算するために並列プラットフォーム実行で使用されるプロセッサの数。このステップで実際に使用されるプロセッサの数は、実行の総プロセッサ数（MPIサイズ）とsm*number*processorsの最小値になります。デフォルトは`1`。
  * `near_field_translation_distance`: [**MSTM v3**] 近接場計算から遠方場計算への変換の閾値。

      * 最大球間$kr$（すなわち、十分に大きな数、例えば1e6）より大きい値は、すべての球が近接場セットに属することを引き起こします。
      * 最小球間$kr$（すなわち、ゼロ）より小さい値は、すべての球が遠方場セットに属することを引き起こします。
      * 負の値は自動基準を有効にします：

    $$
    kr_{i-j}\le\left[\frac{1}{2}(L_i+L_j)^2\right]
    $$

    デフォルトは`1e6`で、これはすべての球が互いの近接場内にあると見なされることを意味します。
  * `iterations_per_correction`: [**MSTM v3**] 特定の修正段階のための最大BCGM反復回数。デフォルトは`20`。遠方場セットに属する球対がいくつかある場合にのみ機能します。
  * `θ_min`: [**MSTM v3**] 最小散乱極角。デフォルトは`0.0`。
  * `θ_max`: [**MSTM v3**] 最大散乱極角。デフォルトは`180.0`。
  * `ϕ_min`: [**MSTM v3**] 最小散乱方位角。デフォルトは`0.0`。
  * `ϕ_max`: [**MSTM v3**] 最大散乱方位角。デフォルトは`0.0`。
  * `Δθ`: [**MSTM v3**, **MSTM v4**] 散乱行列計算のためのθの間隔。デフォルトは`1.0`。
  * `Δϕ`: [**FaSTMM**] 散乱行列計算のためのϕの間隔。デフォルトは`10.0`。
  * `frame`: [**MSTM v3**, **MSTM v4**] 散乱角が基づく参照座標系を選択します。

      * `IncidentFrame`、フレームは入射場に基づいており、`θ = 0`は前方散乱方向（すなわち、入射場の伝播方向）で、`θ = β, φ = 180`はターゲットのz軸方向です。
      * `TargetFrame`、フレームはターゲットフレームに基づいており、`θ = 0`はターゲットのz軸に対応し、`θ = β, φ = α`は入射場の方向です。false。ランダム方向計算はこのオプションを強制します。
  * `normalize_scattering_matrix`: [**MSTM v3**, **MSTM v4**] 散乱行列を正規化するかどうか。デフォルトは`true`。**MSTM v3**では、このオプションは他の行列要素をS11に従って正規化します。**MSTM v4**では、他の要素は常にS11に正規化され、このオプションはS11自体の正規化を制御します。
  * `azimuthal_average`: [**MSTM v3**, **MSTM v4**] 固定方向計算のために方位平均を取るかどうか。デフォルトは`false`。
  * `single_origin_expansion`: [**MSTM v4**] 散乱電場を単一の起源で再展開するかどうか。デフォルトは`true`。`azimuthal_average`が`true`の場合、このオプションはオンにする必要があります。フラクタル集積体のようなまばらな球に対しては、このオプションをオフにすることをお勧めします。
  * `gaussian_beam_constant`: [**MSTM v3**, **MSTM v4**] 入射ガウスプロファイルビームの焦点での無次元逆幅CB。`0`に設定すると平面波入射が選択されます。ガウスビームを表すために使用される局所近似は、CB ≤ 0.2のときに正確です。デフォルトは`0.0`（平面波）。
  * `gaussian_beam_focal_point`: [**MSTM v3**, **MSTM v4**] `spheres`によって定義された原点に対するガウスビームの焦点のx、y、z座標。デフォルトは`(0.0, 0.0, 0.0)`。
  * `orientation`: [**MSTM v3**, **MSTM v4**]

      * 固定方向計算には`FixedOrientation`を使用します。
      * ランダム方向計算には`RandomOrientation`を使用します。

    デフォルトは`FixedOrientation`。
  * `use_monte_carlo_integration`: [**MSTM v4**] 解析平均の代わりにモンテカルロ積分を使用するかどうか。デフォルトは`false`。
  * `number_incident_directions`: [**MSTM v4**] モンテカルロ積分に使用される方向の数。`use_monte_carlo_integration = true`のときのみ機能します。デフォルトは`100`。
  * `α`: 入射波の方位角（度）。デフォルトは`0.0`。
  * `β`: 入射波の極角（度）。デフォルトは`0.0`。
  * `calculate_scattering_matrix`: [**MSTM v4**] 散乱行列を計算するかどうか。デフォルトは`true`。
  * `calculate_scattering_coefficients`: [**MSTM v3**] 散乱係数を計算するかどうか。デフォルトは`true`。`= false`の場合、散乱係数は`scattering_coefficient_file`で指定されたファイルから読み込まれます。
  * `scattering_coefficient_file`: [**MSTM v3**] 散乱係数ファイルのファイル名。デフォルトは`"mstm.scat"`。

      * `calculate_scattering_coefficients = false`の場合、散乱係数はこのファイルから読み込まれます。
      * `calculate_scattering_coefficients = true`の場合、散乱係数はこのファイルに書き込まれます。
  * `use_fft_translation`: [**MSTM v4**] FFTベースの加速アルゴリズムを使用するかどうか。デフォルトは`false`。
  * `cell_volume_fraction`: [**MSTM v4**] アルゴリズムで使用される立方格子のグリッドサイズ$d$を決定します。式は次のとおりです：

    $$
    d=\left(\frac{V_S}{cN_{s,ext}}\right)^{1/3}
    $$

    ここで、$V_S$は外部球の無次元総体積、$c$は`cell_volume_fraction`です。最適な値は通常、ノードの総数が外部球の総数NS,extに近いところです。`cell_volume_fraction = 0`に設定すると、球の体積分率の推定を使用してdの設定が自動化されます。デフォルトは`0.0`。`use_fft_translation = true`のときのみ機能します。
  * `node_order`: [**MSTM v4**] 散乱場のノードベースの展開の切断次数。`node_order = −L`に設定すると、ノードの次数は`ceil(d) + L`に設定されます。デフォルトは`-1`。`use_fft_translation = true`のときのみ機能します。
  * `scattering_map_model`: [**MSTM v4**] `= 0`は、散乱行列を極角（θ）の範囲で印刷し、角度の増分は`Δθ`で与えられます。散乱平面は入射方位平面と一致します。θの制限は平面境界の数NBに依存します。`scattering_map_model = 1`は、散乱行列を2D配列のペア（cosθ > 0, < 0）で印刷し、座標は`kx = sinθcosφ`、`ky = sinθsinφ`です。各軸のポイント数は`scattering_map_dimension`で与えられます。デフォルトは`0`で、ランダム方向計算は`0`を強制します。
  * `scattering_map_dimension`: [**MSTM v4**] 各軸のポイント数。デフォルトは`15`。`scattering_map_model = 1`のときのみ機能します。
  * `track_iterations`: [**MSTM v3**] 各反復の誤差を実行印刷ファイルに印刷するかどうか。デフォルトは`true`。
  * `calculate_near_field`: [**MSTM v3**, **MSTM v4**] 近接場を計算するかどうか。デフォルトは`false`。
  * `near_field_plane_coord`: [**MSTM v3**] 近接場平面の座標。`1` = y-z, `2` = z-x, `3` = x-y。デフォルトは`1`。
  * `near_field_plane_position`: [**MSTM v3**] 近接場平面の位置。

      * `near_field_plane_coord = 1`の場合、これはx座標です。
      * `near_field_plane_coord = 2`の場合、これはy座標です。
      * `near_field_plane_coord = 3`の場合、これはz座標です。

    デフォルトは`0.0`。
  * `near_field_plane_vertices`: [**MSTM v3**] 近接場平面の長方形領域。

      * `(ΔX, ΔY)`を渡すと、実際の領域は`(X_min-ΔX, X_max+ΔX) x (Y_min-ΔY, Y_max+ΔY)`となり、`X_min`、`X_max`、`Y_min`、`Y_max`は自動的に計算されます。
      * `(X_min, Y_min, X_max, Y_max)`を渡すと、その領域がそのまま使用されます。

    デフォルトは`(0.0, 0.0)`。
  * `near_field_x_min`: [**MSTM v4**] 近接場計算領域の最小x座標。デフォルトは`0.0`。
  * `near_field_x_max`: [**MSTM v4**] 近接場計算領域の最大x座標。デフォルトは`0.0`。
  * `near_field_y_min`: [**MSTM v4**] 近接場計算領域の最小y座標。デフォルトは`0.0`。
  * `near_field_y_max`: [**MSTM v4**] 近接場計算領域の最大y座標。デフォルトは`0.0`。
  * `near_field_z_min`: [**MSTM v4**] 近接場計算領域の最小z座標。デフォルトは`0.0`。
  * `near_field_z_max`: [**MSTM v4**] 近接場計算領域の最大z座標。デフォルトは`0.0`。
  * `near_field_step_size`: [**MSTM v3**, **MSTM v4**] グリッドポイントの空間ステップサイズ。デフォルトは`0.1`。
  * `near_field_calculation_model`: [**MSTM v4**] 計算結果における入射場の出現場所を制御します；`= 1`は標準モデルで、外部場は散乱場 + 入射場であり、球内の場は内部場展開から計算されます；`≠ 1`は外部場が散乱場のみによるもので、粒子内の場は内部-入射場になります。デフォルトは`1`。
  * `polarization_angle_deg`: [**MSTM v3**] 近接場を計算するために必要な入射場の特定の偏光状態。場は線形偏光と見なされ、k–z平面に対する偏光角`γ`を持ちます。`β = 0`のとき、`γ`はクラスター座標系に対する入射電場ベクトルの方位角になります。デフォルトは`0.0`。
  * `store_surface_vector`: [**MSTM v4**] フィールド値の計算のための加速アルゴリズムを有効にするかどうか。デフォルトは`true`。
  * `near_field_expansion_spacing`: [**MSTM v4**] 平面境界および周期格子相互作用からの場の再展開に使用されるグリッドのサイズ。デフォルトは`5.0`。計算が長すぎる場合はこれを試してみてください。`store_surface_vector = true`のときのみ機能します。
  * `near_field_expansion_order`: [**MSTM v4**] 上記のオプションに従った二次場のグリッド再展開に使用される展開切断次数。Mie型基準に従ってnear*field*expansion*spacingにスケールする必要があります。値が大きいほど結果は正確になりますが、計算は遅くなり、メモリの要求が増えます。デフォルトは`10`。`store*surface_vector = true`のときのみ機能します。
  * `near_field_output_file`: [**MSTM v3**, **MSTM v4**] 近接場出力のファイル名。デフォルトは`"mstm.nf"`。
  * `plane_wave_epsilon`: [**MSTM v3**] 近接場計算のための入射場成分 – 平面波またはガウスビームモデルのいずれか – は、ビーム焦点を中心にした単一の通常のVSWF展開を使用して計算されます。平面波のepsilonはこの展開の収束基準です。デフォルトは`1e-4`。
  * `calculate_t_matrix`: [**MSTM v3**] T行列を計算するオプションまたは既存のT行列ファイルを使用するオプション。デフォルトは`true`で、T行列を計算します。
  * `t_matrix_file`: [**MSTM v3**]

      * `calculate_t_matrix = true`の場合、これはT行列出力のファイル名です。
      * `calculate_t_matrix = false`の場合、これはT行列を読み込むためのファイル名です。

    デフォルトは`"mstm.tm"`。
  * `layers`: [**MSTM v3**, **MSTM v4**] 媒体層。

      * **MSTM v3**の場合、最初の層の屈折率とキラル因子のみが使用されます。厚さは無視されます。
      * **MSTM v4**の場合、最初の層は`z=0`に位置し、`-∞`まで拡張します。最後の層は`+∞`まで拡張します。最初と最後の層の厚さは無視されます。
  * `spheres`: [**MSTM v3**, **MSTM v4**] 球体。
  * `periodic`: [**MSTM v4**] `periodic = true`の場合、球体はx-y平面に周期格子を構築するものと見なされます。周期格子はランダム方向と互換性がないことに注意してください。
  * `cell_size`: [**MSTM v4**] `periodic = true`の場合、このオプションは周期格子のサイズを設定します。すべての球体を含むことができない場合、セルサイズは自動的に拡大されます。
  * `redirect_stdout`: プログラムの出力を指定されたIOストリームにリダイレクトします。デフォルトは`Base.stdout`。
