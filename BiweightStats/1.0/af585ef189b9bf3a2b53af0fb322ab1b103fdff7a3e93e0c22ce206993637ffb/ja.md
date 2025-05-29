```
BiweightStats
```

ロバスト統計に基づくモジュールで、バイウェイト変換を使用します。[^1]

# バイウェイト統計

バイウェイト変換の基礎はロバスト分析であり、これは外れ値に対して強靭でありながら、さまざまな基礎分布を効率的に表現する統計です。バイウェイト変換は*中央値*と*中央値絶対偏差 (MAD)* に基づいています。中央値は位置のロバスト推定量であり、MADはスケールのロバスト推定量です。

$$
\mathrm{MAD}(X) = \mathrm{median}\left|X_i - \bar{X}\right|
$$

ここで、$\bar{X}$は中央値です。

バイウェイト変換は、重要なカットオフを超えるデータをフィルタリングすることによって、これらの推定を改善します。このアナロジーは、標準偏差と平均の代わりにこれらのロバスト統計を使用してシグマフィルタを行うことです。

$$
u_i = \frac{X_i - \bar{X}}{c \cdot \mathrm{MAD}}
$$

$$
\forall i \quad\mathrm{where}\quad u_i^2 \le 1
$$

カットオフ因子$c$は、1.4826[^2]を掛けることによってガウス標準偏差に直接関連付けることができます。したがって、典型的な$c=9$の値は、$13.3\sigma$よりも遠い外れ値がクリップされることを意味します（真にガウス分布している残差の場合）。さらに、`BiweightStats`では、`NaN`や`Inf`もスキップします（ただし、`missing`や`nothing`はスキップしません）。

# 参考文献

[^1]: [NIST: biweight](https://www.itl.nist.gov/div898/software/dataplot/refman2/ch2/biweight.pdf)

[^2]: [中央値絶対偏差](https://en.wikipedia.org/wiki/Median_absolute_deviation#Relation_to_standard_deviation)

# メソッド

  * [`location`](@ref)
  * [`scale`](@ref)
  * [`midvar`](@ref)
  * [`midcov`](@ref)
  * [`midcor`](@ref)
