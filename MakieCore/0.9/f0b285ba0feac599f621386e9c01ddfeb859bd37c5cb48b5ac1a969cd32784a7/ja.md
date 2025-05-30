```
volume(volume_data)
volume(x, y, z, volume_data)
```

物理的な次元 `x, y, z` をオプションとして持つボリュームをプロットします。

すべてのボリュームプロットは、描画された各ピクセルのためにレイをキャストすることから派生しています。これらのレイはボリュームデータと交差し、通常は与えられたカラーマップに基づいていくつかの色を導き出します。色がどのように導き出されるかは、使用されるアルゴリズムによって異なります。

## プロットタイプ

`volume` 関数のプロットタイプエイリアスは `Volume` です。

## 属性

**`absorption`** =  `1.0`  — アルゴリズム = :absorption, :absorptionrgba および :indexedabsorption のための吸収倍率。これは各ボクセルがどれだけの光を吸収するかを変更します。

**`algorithm`** =  `:mip`  — 使用されるボリュームアルゴリズムを設定します。利用可能なアルゴリズムは次のとおりです：

  * `:iso`: 与えられた浮動小数点データ内の等値面を表示します。これには `isovalue - isorange .. isovalue + isorange` 内のサンプルのみがピクセルの最終色に含まれます。
  * `:absorption`: ボリュームデータからサンプリングされた浮動小数点値に基づいて色を蓄積します。各レイステップ（前方から開始）で、ボリュームデータから値がサンプリングされ、その後カラーマップをサンプリングするために使用されます。結果の色はレイステップサイズによって重み付けされ、以前に蓄積された色とブレンドされます。各ステップの重みは乗算的な `absorption` 属性で調整できます。
  * `:mip`: 与えられた浮動小数点データの最大強度投影を表示します。これは、各レイからサンプリングされた最大値からピクセルの色を導き出します。
  * `:absorptionrgba`: このアルゴリズムは :absorption と一致しますが、RGBAボリュームデータから直接色をサンプリングします。各レイステップでデータから色がサンプリングされ、レイステップサイズによって重み付けされ、以前に蓄積された色とブレンドされます。また、`absorption` を考慮します。
  * `:additive`: `accumulated_color = 1 - (1 - accumulated_color) * (1 - sampled_color)` を使用して色を蓄積します。ここで `sampled_color` は現在のレイステップでのボリュームデータのサンプルです。
  * `:indexedabsorption`: このアルゴリズムは :absorption と同様に動作しますが、ボリュームデータをインデックスとして解釈します。これらはカラーマップへの直接インデックスとして使用されます。また、`absorption` を考慮します。

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファは乗算されます。

**`backlight`** =  `0.0`  — 反転法線を持つ二次光計算の重みを設定します。

**`clip_planes`** =  `automatic`  — クリップ平面は3D空間でクリッピングを行う方法を提供します。ここに最大8つの `Plane3f` 平面のベクトルを設定でき、その後ろでプロットがクリップされます（つまり、見えなくなります）。デフォルトではクリップ平面は親プロットまたはシーンから継承されます。`Plane3f[]` を渡すことで親の `clip_planes` を削除できます。

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラースケールを確認するには、`Makie.available_gradients()` を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar` と一緒に `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。

**`depth_shift`** =  `0.0`  — すべての他の変換後にプロットの深度値を調整します。すなわち、クリップ空間で、`-1 <= depth <= 1` の範囲です。これは GLMakie と WGLMakie のみに適用され、レンダリング順序を調整するために使用できます（調整可能なオーバードローのように）。

**`diffuse`** =  `1.0`  — 赤、緑、青の各チャンネルが拡散（散乱）光にどれだけ強く反応するかを設定します。

**`enable_depth`** =  `true`  — :iso のために深度書き込みを有効にし、ボリュームが他のオブジェクトを正しく隠すようにします。

**`fxaa`** =  `true`  — プロットが fxaa（アンチエイリアス、GLMakie のみ）でレンダリングされるかどうかを調整します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`inspectable`** =  `@inherit inspectable`  — このプロットが `DataInspector` に表示されるべきかどうかを設定します。デフォルトは親シーンのテーマに依存します。

**`inspector_clear`** =  `automatic`  — DataInspector 内のカスタムインジケーターをクリーンアップするためのコールバック関数 `(inspector, plot) -> ...` を設定します。

**`inspector_hover`** =  `automatic`  — デフォルトの `show_data` メソッドを置き換えるコールバック関数 `(inspector, plot, index) -> ...` を設定します。

**`inspector_label`** =  `automatic`  — DataInspector によって生成されるデフォルトのラベルを置き換えるコールバック関数 `(plot, index, position) -> string` を設定します。

**`interpolate`** =  `true`  — ボリュームデータが補間を使用してサンプリングされるべきかどうかを設定します。

**`isorange`** =  `0.05`  — :iso アルゴリズムのために等値から受け入れられる最大距離を設定します。`accepted = isovalue - isorange < value < isovalue + isorange`

**`isovalue`** =  `0.5`  — :iso アルゴリズムのためのターゲット値を設定します。`accepted = isovalue - isorange < value < isovalue + isorange`

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`material`** =  `nothing`  — 複雑なRadeonProRenderマテリアルを設定するためのRPRMakie専用属性。         *警告*、RPRマテリアルの設定方法は変更される可能性があり、他のバックエンドはこの属性を無視します。

**`model`** =  `automatic`  — プロットのモデル行列を設定します。これは `translate!`、`rotate!` および `scale!` で行われた調整を上書きします。

**`nan_color`** =  `:transparent`  — NaN 値の色。

**`overdraw`** =  `false`  — プロットが他のプロットの上に描画されるかどうかを制御します。これは特に GL バックエンドで深度チェックを無視することを意味します。

**`shading`** =  `automatic`  — 使用される照明アルゴリズムを設定します。オプションは `NoShading`（照明なし）、`FastShading`（AmbientLight + PointLight）または `MultiLightShading`（複数の光、GLMakie のみ）です。これは RPRMakie には影響しません。

**`shininess`** =  `32.0`  — 反射の鋭さを設定します。

**`space`** =  `:data`  — プロットを包含するボックスの変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

**`specular`** =  `0.2`  — オブジェクトが赤、緑、青の各チャンネルで光をどれだけ強く反射するかを設定します。

**`ssao`** =  `false`  — プロットが ssao（スクリーンスペース環境オクルージョン）でレンダリングされるかどうかを調整します。これは3Dプロットでのみ意味があり、`fxaa = true` の場合にのみ適用されます。

**`transformation`** =  `:automatic`  — *ドキュメントは利用できません。*

**`transparency`** =  `false`  — プロットが透明性をどのように扱うかを調整します。GLMakie では `transparency = true` は順序独立透明性を使用する結果になります。

**`visible`** =  `true`  — プロットがレンダリングされるかどうかを制御します。
