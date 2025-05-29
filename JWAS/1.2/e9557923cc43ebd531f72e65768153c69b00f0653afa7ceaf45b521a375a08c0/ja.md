```
build_model(model_equations::AbstractString,R=false; df::AbstractFloat=4.0)
```

  * **モデル方程式**からモデルを構築し、残差分散**R**を指定します。ベイズ分析では、**R**は残差分散に対して割り当てられた事前分布の平均であり、自由度**df**はデフォルトで4.0です。**R**が提供されていない場合、応答（表現型）から値が計算されます。
  * デフォルトでは、model*equations内のすべての変数は因子（カテゴリカル）であり、固定されています。変数を共変量（連続）またはランダムに設定するには、`set*covariate()`または`set_random()`関数を使用します。

```julia
#単一形質
model_equations = "BW = intercept + age + sex"
R               = 6.72
models          = build_model(model_equations,R);

#多重形質
model_equations = "BW = intercept + age + sex
                   CW = intercept + litter";
R               = [6.72   24.84
                   24.84  708.41]
models          = build_model(model_equations,R);
```
