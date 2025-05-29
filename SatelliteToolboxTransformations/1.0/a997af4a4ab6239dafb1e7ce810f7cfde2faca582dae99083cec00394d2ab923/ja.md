```
r_cirs_to_tirs_iau2006([T, ]jd_ut1::Number) -> T
```

天体中間基準系 (CIRS) を地球中間基準系 (TIRS) に合わせる回転を、ユリウス日 `jd_ut1` [UT1] で計算します。このアルゴリズムはIAU-2006理論を使用しています。

回転のタイプはオプションの変数 `T` によって説明されます。もし `DCM` であれば、DCM が返されます。そうでなければ、`Quaternion` であれば、Quaternion が返されます。このパラメータが省略された場合、`DCM` にフォールバックします。

# 戻り値

CIRSフレームをTIRSフレームに合わせる回転。回転の表現はオプションのパラメータ `T` によって選択されます。

# 備考

TIRSとCIRSの基準フレームは、地球回転角に関するZ軸周りの回転によって分離されており、これは従来の国際原点 (CIO) と地球中間原点 (TIO) の間の角度です **[1]**。後者は、天体中間極 (CIP) の赤道に沿ってグリニッジ子午線から約100m離れた位置にある地球上の基準子午線です **[1]**。

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications.  Microcosm   Press, Hawthorn, CA, USA.
