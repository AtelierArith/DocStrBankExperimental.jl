```
estimate(be; estimator = "auto", method = "auto", supresswarn = false)
```

`method` - Model settings.

  * if `method == "auto"` than method `A` used for "2X2" and "2X2X2"  designes, method `P` for "parallel" design and method `B` for any other.

*Methods:*

  * `A` using GLM and model `@formula(var ~ formulation + period + sequence + subject)`
  * `B` using MixedModels and model `@formula(var ~ formulation + period + sequence + (1|subject))` or Metida and model `@lmmformula(v ~ formulation + period + sequence, random = 1|subject:SI)`
  * `C` using Metida and model `@lmmformula(v ~ formulation + period + sequence, random = formulation|subject:CSH, repeated = formulation|subject:DIAG)`
  * `P` using GLM and model `@formula(var ~ formulation)`

`estimator` - Estimator settings.

  * if `estimator == "auto"` than GLM used for "parallel" design; for "2X2" design used GLM if no droputs and MixedModels if `dropout == true`; for other designes with method `C` Metida used and MixedModel for other cases.

*Estimators:*

  * "glm" for GLM (https://juliastats.org/GLM.jl/stable/)
  * "mm" for MixedModels (https://juliastats.org/MixedModels.jl/stable/)
  * "met" for Metida (https://pharmcat.github.io/Metida.jl/stable/)

*Other autosettings:*

If design is "parallel" `estimator` set as "glm" and `method` as "P".

If design is "2X2" and method is "P" or "C" than if `estimator` == "glm" method set as "A" and "B" for other estimators. 

If design not "parallel" or "2X2": 

if method not "A", "B" or "C" than set as "A" for "glm" ann as B for other estimators;

if `estimator` == "glm" and `method` == "B" than `estimator` set as "mm", if `estimator` == "glm" or "mm" and `method` == "C" than `estimator` set as "met".

Reference:

EMA: [GUIDELINE ON THE INVESTIGATION OF BIOEQUIVALENCE](https://www.ema.europa.eu/en/documents/scientific-guideline/guideline-investigation-bioequivalence-rev1_en.pdf)

EMA: [GUIDELINE ON THE INVESTIGATION OF BIOEQUIVALENCE, Annex I](https://www.ema.europa.eu/en/documents/other/31-annex-i-statistical-analysis-methods-compatible-ema-bioequivalence-guideline_en.pdf)
