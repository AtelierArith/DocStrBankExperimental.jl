```
modelfit(y, yh)
```

`yh`と`y`のモデルフィットをパーセンテージで計算します。これは、正規化された二乗平均平方根誤差（NRMSE）とも呼ばれます。

$$
\text{modelfit}(y, \hat{y}) = 100 \left(1 - \frac{\sqrt{\text{SSE}(y - \hat{y})}}{\sqrt{\text{SSE}(y - \bar{y})}}\right)
$$

出力が100の場合は完璧なフィットを示し、出力が0の場合はデータの平均と同じ程度のフィットであることを示します。予測がデータの平均を予測するよりも悪い場合、負の値が出ることがあります。

関連情報としては、[`rms`](@ref)、[`sse`](@ref)、[`mse`](@ref)、[`fpe`](@ref)、[`aic`](@ref)があります。
