```
value_at_risk(returns, confidence, method; multiplier=1.0)
```

指定された推定方法に基づいて、特定の有意水準 `α` のバリュー・アット・リスク (VaR) を計算します。VaR 値は、特定の有意水準 `α` での最大期待損失を表します。よりテールリスクに焦点を当てた指標については、`expected_shortfall` を参照してください。

# 引数

  * `returns`:     資産のリターンのベクトル。
  * `α`:           有意水準。例えば、95% の信頼度には `0.05` を、99% の信頼度には `0.01` を使用します。
  * `method`:      分布推定方法： `:historical`、 `:gaussian` または `:cornish_fisher`。
  * `multiplier`:  オプションのスカラー乗数。例えば、月次リターンを年換算するには `12` を使用し、日次リターンを年換算するには `252` を使用します。

# 方法

  * `:historical`:        リターンの経験的分布に基づく歴史的手法。
  * `:gaussian`:          パラメトリックフィット（平均、分散）に基づくガウス分布。
  * `:cornish_fisher`:    第三および第四モーメント（歪度、尖度）に調整されたガウスパラメトリック分布フィットに基づくコーニッシュ・フィッシャー。コーニッシュ・フィッシャー展開は、真の分布の分位点を近似することを目的としており、その分布の高次モーメント（歪度と尖度）を使用して非正規性を調整します。詳細については https://thema.u-cergy.fr/IMG/pdf/2017-21.pdf を参照してください。

# 出典

  * Favre, Laurent and Galeano, Jose-Antonio (2002). Mean-Modified Value-at-Risk Optimization with Hedge Funds. Journal of Alternative Investment.
  * Amédée-Manesme, Charles-Olivier and Barthélémy, Fabrice and Maillard, Didier (2017). Computation of the Corrected Cornish–Fisher Expansion using the Response Surface Methodology: Application to VaR and CVaR. THEMA Working Paper n°2017-21, Université de Cergy-Pontoise, France.
