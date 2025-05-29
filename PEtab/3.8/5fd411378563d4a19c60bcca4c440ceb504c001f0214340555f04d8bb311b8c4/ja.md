```
PEtabObservable(obs_formula, noise_formula; kwargs...)
```

モデル出力と測定データを結びつける尤度を定義する式。

`obs_formula` はモデル出力が測定データにどのように関連するかを説明し、`noise_formula` は標準偏差（測定誤差）を説明し、方程式または数値値であることができます。可観測量とノイズの式は、いずれも有効なJuliaの方程式である必要があります。これらの式で使用される変数は、モデル種、モデルパラメータ、または `PEtabParameter` として定義されたパラメータでなければなりません。式には、時間点特有のノイズおよび可観測量パラメータも含めることができます。詳細については、ドキュメントを参照してください。

## キーワード引数

  * `transformation`: 可観測量とその対応する測定に適用される変換。 有効なオプションは `:lin`（通常の測定ノイズ）、`:log`、`log2` または `:log10`（対数正規測定ノイズ）です。詳細については以下を参照してください。

## 説明

測定 `y`、可観測量 `h = obs_formula`、および標準偏差 `σ = noise_formula` に対して、`PEtabObservable` はモデル出力と測定データを結びつける尤度を定義します: $\pi(y \mid h, \sigma)$。`transformation = :lin` の場合、測定ノイズは正規分布していると仮定され、尤度は次のように与えられます：

$$
\pi(y|h, \sigma) = \frac{1}{\sqrt{2\pi \sigma^2}}\mathrm{exp}\bigg( -\frac{(y - h)^2}{2\sigma^2} \bigg)
$$

特別な場合として、$\sigma = 1$ の場合、この尤度は最小二乗目的関数に簡約されます。`transformation = :log` の場合、測定ノイズは対数正規分布していると仮定され、尤度は次のように与えられます：

$$
\pi(y|h, \sigma) = \frac{1}{\sqrt{2\pi \sigma^2 y^2}}\mathrm{exp}\bigg( -\frac{\big(\mathrm{log}(y) - \mathrm{log}(h)\big)^2}{2\sigma^2} \bigg)
$$

`transformation = :log10` の場合、測定ノイズはlog10正規分布していると仮定され、尤度は次のように与えられます：

$$
\pi(y|h, \sigma) = \frac{1}{\sqrt{2\pi \sigma^2 y^2}\mathrm{log}(10) }\mathrm{exp}\bigg( -\frac{\big(\mathrm{log}_{10}(y) - \mathrm{log}_{10}(h)\big)^2}{2\sigma^2} \bigg)
$$

最後に、`transformation = :log2` の場合、測定ノイズはlog2正規分布していると仮定され、尤度は次のように与えられます：

$$
\pi(y|h, \sigma) = \frac{1}{\sqrt{2\pi \sigma^2 y^2}\mathrm{log}(2) }\mathrm{exp}\bigg( -\frac{\big(\mathrm{log}_{2}(y) - \mathrm{log}_{2}(h)\big)^2}{2\sigma^2} \bigg)
$$

数値的安定性のために、PEtab.jlは実際には対数尤度で動作します。
