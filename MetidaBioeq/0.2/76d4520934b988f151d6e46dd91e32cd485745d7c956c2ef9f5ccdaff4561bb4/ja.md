```
estimate(be; estimator = "auto", method = "auto", supresswarn = false)
```

`method` - モデル設定。

  * `method == "auto"` の場合、"2X2" および "2X2X2" デザインにはメソッド `A` が使用され、"parallel" デザインにはメソッド `P` が使用され、その他のデザインにはメソッド `B` が使用されます。

*メソッド:*

  * `A` は GLM を使用し、モデル `@formula(var ~ formulation + period + sequence + subject)`
  * `B` は MixedModels を使用し、モデル `@formula(var ~ formulation + period + sequence + (1|subject))` または Metida を使用し、モデル `@lmmformula(v ~ formulation + period + sequence, random = 1|subject:SI)`
  * `C` は Metida を使用し、モデル `@lmmformula(v ~ formulation + period + sequence, random = formulation|subject:CSH, repeated = formulation|subject:DIAG)`
  * `P` は GLM を使用し、モデル `@formula(var ~ formulation)`

`estimator` - 推定器設定。

  * `estimator == "auto"` の場合、"parallel" デザインには GLM が使用されます；"2X2" デザインにはドロップアウトがない場合は GLM が使用され、`dropout == true` の場合は MixedModels が使用されます；メソッド `C` のその他のデザインには Metida が使用され、その他のケースには MixedModel が使用されます。

*推定器:*

  * "glm" は GLM 用 (https://juliastats.org/GLM.jl/stable/)
  * "mm" は MixedModels 用 (https://juliastats.org/MixedModels.jl/stable/)
  * "met" は Metida 用 (https://pharmcat.github.io/Metida.jl/stable/)

*その他の自動設定:*

デザインが "parallel" の場合、`estimator` は "glm" に、`method` は "P" に設定されます。

デザインが "2X2" で、メソッドが "P" または "C" の場合、`estimator` が "glm" の場合はメソッドが "A" に設定され、その他の推定器には "B" が設定されます。

デザインが "parallel" または "2X2" でない場合：

メソッドが "A"、"B" または "C" でない場合、"glm" には "A" が、その他の推定器には "B" が設定されます；

`estimator` が "glm" で、`method` が "B" の場合、`estimator` は "mm" に設定され、`estimator` が "glm" または "mm" で、`method` が "C" の場合、`estimator` は "met" に設定されます。

参考文献:

EMA: [GUIDELINE ON THE INVESTIGATION OF BIOEQUIVALENCE](https://www.ema.europa.eu/en/documents/scientific-guideline/guideline-investigation-bioequivalence-rev1_en.pdf)

EMA: [GUIDELINE ON THE INVESTIGATION OF BIOEQUIVALENCE, Annex I](https://www.ema.europa.eu/en/documents/other/31-annex-i-statistical-analysis-methods-compatible-ema-bioequivalence-guideline_en.pdf)
