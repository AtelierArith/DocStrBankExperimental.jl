```
r_teme_to_pef([T, ]jd_tt::Number) -> T
```

真の赤道平均春分点 (TEME) フレームを擬似地球固定 (PEF) フレームに合わせる回転を、ユリウス日 `jd_tt` [地球時間] で計算します。このアルゴリズムは、IAU-76/FK5 理論と **[1]**(p.  233) の TEME 定義を使用しています。

回転のタイプは、オプションの変数 `T` によって説明されます。もしそれが `DCM` であれば、DCM が返されます。そうでなければ、`Quaternion` であれば、Quaternion が返されます。このパラメータが省略された場合、`DCM` にフォールバックします。

# 戻り値

  * `T`: TEME フレームを PEF フレームに合わせる回転。

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.

```
