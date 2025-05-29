```
ccolon
```

`ccolon`データセットは、フランスからの相対生存データセットの例を提供し、`RateTables.jl`パッケージの`survexp_fr`レートテーブルとペアにする必要があります。以下の列が含まれています：

  * `time`、日数：診断からのフォローアップ時間、
  * `status`、ブール値：観察された死亡（1）または検閲（0）、
  * `age`、日数：診断時の年齢、
  * `year`、0000-00-00からの日数：診断日、
  * `sex`、`:male`または`:female`、
  * `stage`、0から3の整数、診断時の癌TNM（腫瘍リンパ節転移）ステージに対応し、I、II、III、IIIbまたはIVのいずれか。
  * `side`、主要な腫瘍の位置、結腸の`:right`または`:left`のいずれか。

このデータセットは、[Giorgi2003](@cite)、[Wolski2020](@cite)、および[Laverny2025](@cite)で研究されています。これは、1976年から1990年の間に診断されたブルゴーニュの消化器癌登録からの大腸癌の症例に関する人口ベースの生存データを含んでいます。患者は1) 10年間のフォローアップ後および2) 1994年12月31日に検閲されました。収集された元のデータは、プライバシーの目的と法的理由のためにわずかに修正されました。このデータの摂動のため、日付や年齢は厳密にその実際の元の値に対応していません。このデータセットはしたがって、教育的および方法論的な例として提供されており、医療研究の目的で使用すべきではありません。

参考文献：

  * [Giorgi2003](@cite) Giorgi, Roch and Abrahamowicz, Michal and Quantin, Catherine and Bolard, Philippe and Esteve, Jacques and Gouvernet, Joanny and Faivre, Jean. A relative survival regression model using B-spline functions to model non-proportional hazards. Statistics in medicine
  * [Wolski2020](@cite) Wolski, Anna and Graff{'e}o, Nathalie and Giorgi, Roch and {the CENSUR working survival group}. A Permutation Test Based on the Restricted Mean Survival Time for Comparison of Net Survival Distributions in Non-Proportional Excess Hazard Settings. Statistical Methods in Medical Research.
  * [Laverny2025](@cite) Laverny, O., Grafféo, N., & Giorgi, R. (2025). Non-parametric estimation of net survival under dependence between death causes. arXiv preprint arXiv:2502.09273.
