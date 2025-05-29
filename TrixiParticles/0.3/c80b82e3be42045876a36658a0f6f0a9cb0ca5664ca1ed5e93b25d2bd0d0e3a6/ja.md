```
KernelCorrection()
```

カーネル補正は、[Bonet (1999)](@cite Bonet1999)によって説明されているように、シェパード補間を使用して0次精度の結果を得るもので、これはLi et al.によって最初に提案されました。これは、[Basa et al. (2008)](@cite Basa2008)によって示されるように、カーネル補正勾配を得るためにさらに拡張できます。

カーネル補正係数は次のように決定されます。

$$
c(x) = \sum_{b=1} V_b W_b(x)
$$

補正されたカーネルの勾配は次のように決定されます。

$$
\nabla \tilde{W}_{b}(r) =\frac{\nabla W_{b}(r) - W_b(r) \gamma(r)}{\sum_{b=1} V_b W_b(r)} , \quad  \text{where} \quad
\gamma(r) = \frac{\sum_{b=1} V_b \nabla W_b(r)}{\sum_{b=1} V_b W_b(r)}.
$$

この補正は[`SummationDensity`](@ref)および[`ContinuityDensity`](@ref)と共に適用でき、特に自由表面での改善につながります。

!!! note
      * これは、境界モデルが[`SummationDensity`](@ref)を使用している場合にのみ機能します（まだ）。
      * これは「0次補正」とも呼ばれます。
      * 2Dでは、計算時間が約10〜15％増加することが期待できます。

