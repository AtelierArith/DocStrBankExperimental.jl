```
FisherExactTest(a::Integer, b::Integer, c::Integer, d::Integer)
```

帰無仮説の下でのフィッシャーの正確検定を実行します。成功確率 $a/c$ と $b/d$ が等しい、すなわちオッズ比 $(a/c) / (b/d)$ が1であるという仮説に対して、等しくないという対立仮説を検定します。

デフォルトのp値と信頼区間の計算の詳細については、[`pvalue(::FisherExactTest)`](@ref) および [`confint(::FisherExactTest)`](@ref) を参照してください。

コンティンジェンシーテーブルは次のように構成されています：

|  -   | X1  | X2  |
|:----:|:---:|:---:|
| *Y1* |  a  |  b  |
| *Y2* |  c  |  d  |

!!! note
    `show` 関数の出力には、サンプルオッズ比ではなくオッズ比の条件付き最尤推定値が含まれています。これは、フィッシャーの非中心超幾何分布によって与えられる尤度を最大化します。


実装： [`pvalue(::FisherExactTest)`](@ref), [`confint(::FisherExactTest)`](@ref)

# 参考文献

  * Fay, M.P., "フィッシャーの正確検定またはブレイカーの正確検定に一致する信頼区間" の補足資料。生物統計学、ボリューム 11、イシュー 2、2010年4月1日、ページ 373–374、[link](https://doi.org/10.1093/biostatistics/kxp050)

```
