```
ridgelineplot(chains::Chains[, params::Vector{Symbol}]; kwargs...)
```

`chains`内の`params`のサンプルに対してリッジラインプロットを生成します。

デフォルトでは、すべてのパラメータがプロットされます。

## キーワード引数

以下のオプションが利用可能です：

  * `fill_q`（デフォルト：`false`）および `fill_hpd`（デフォルト：`true`）：量子区間（`fill_q = true`）または最高事後密度（HPD）区間（`fill_hpd = true`）の曲線の下の領域を塗りつぶします。`fill_q = false`および`fill_hpd = false`の両方が設定されている場合、曲線の下の全領域が塗りつぶされます。塗りつぶし色が不要な場合は、シリーズ属性で指定する必要があります。これらのオプションは相互に排他的です。
  * `show_mean`（デフォルト：`true`）および `show_median`（デフォルト：`true`）：事後密度推定の平均（`show_mean = true`）または中央値（`show_median = true`）の垂直線をプロットします。両方のオプションが`true`に設定されている場合、両方の線がプロットされます。
  * `show_qi`（デフォルト：`false`）および `show_hpdi`（デフォルト：`true`）：各密度プロットの下部に量子区間（`show_qi = true`）または最大HPD区間（`show_hpdi = true`）をプロットします。これらのオプションは相互に排他的です。
  * `q`（デフォルト：`[0.1, 0.9]`）：`fill_q = true`または`show_qi = true`の場合にプロットに使用される2つの量子。
  * `hpd_val`（デフォルト：`[0.05, 0.2]`）：`fill_hpd = true`または`show_hpdi = true`の場合にプロットされる最高事後密度区間の補完確率質量。

!!! note
    単一のパラメータが提供されると、生成されるプロットは上記のすべての要素を含む密度プロットになります。

