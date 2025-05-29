```
r_pef_to_teme([T, ]jd_tt::Number) -> T
```

擬似地球固定（PEF）フレームを真の赤道平均春分点（TEME）フレームに整列させる回転を、ユリウス日 `jd_tt` [地球時間] で計算します。このアルゴリズムはIAU-76/FK5理論と**[1]**(p. 233)のTEME定義を使用しています。

回転のタイプはオプションの変数 `T` で説明されます。もし `DCM` であれば、DCMが返されます。そうでなければ、`Quaternion` であれば、Quaternionが返されます。このパラメータが省略された場合、`DCM` にフォールバックします。

# 戻り値

  * `T`: PEFフレームをTEMEフレームに整列させる回転。

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.

```
