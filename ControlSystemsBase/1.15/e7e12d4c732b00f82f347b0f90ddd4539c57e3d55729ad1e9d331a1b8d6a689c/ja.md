```
fig = nyquistplot(sys;                Ms_circles=Float64[], Mt_circles=Float64[], unit_circle=false, hz=false, critical_point=-1, kwargs...)
nyquistplot(LTISystem[sys1, sys2...]; Ms_circles=Float64[], Mt_circles=Float64[], unit_circle=false, hz=false, critical_point=-1, kwargs...)
```

`LTISystem`(s)のナイキストプロットを作成します。周波数ベクトル `w` をオプションで提供できます。

  * `unit_circle`: 単位円を表示するかどうか。ナイキスト曲線はゲイン交差周波数で単位円を横切ります。
  * `Ms_circles`: 与えられた感度レベルに対応する円を描画します（半径 `1/Ms` の -1 の周りの円）。`Ms_circles` は数値または数値のベクトルとして提供できます。このような円の外側に留まる設計は、少なくとも `2asin(1/(2Ms))` ラジアンの位相余裕と、少なくとも `Ms/(Ms-1)` のゲイン余裕を持ちます。
  * `Mt_circles`: 与えられた補完感度レベルに対応する円を描画します。`Mt_circles` は数値または数値のベクトルとして提供できます。
  * `critical_point`: 囲みのために重要な点としてマークする実軸上の点
  * `hz=true` の場合、ホバー情報はヘルツで表示され、入力周波数ベクトルは依然として rad/s として扱われます。
  * `balance`: プロットする前にシステムに対して [`balance_statespace`](@ref) を呼び出します。

`kwargs` はプロットへの引数として送信されます。
