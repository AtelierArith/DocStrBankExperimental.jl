```
r_gcrf_to_mj2000_iau2006([T, ]jd_tt::Number = 0) -> T
```

地心天体参照フレーム（GCRF）をJ2000平均赤道フレームに整列させる回転を計算します。このアルゴリズムはIAU-2006理論を使用しています。この回転は日付に依存しないバイアスマトリックスです。ただし、この関数はAPIの互換性を保つために引数`jd_tt`を受け取ります。

回転のタイプはオプションの変数`T`によって説明されます。`DCM`の場合、DCMが返されます。そうでない場合、`Quaternion`の場合はQuaternionが返されます。このパラメータが省略された場合、`DCM`にフォールバックします。

!!! info
    **[1]** によると、MJ2000 <=> GCRFを変換するフレームバイアスは、すべての時刻に対して正確な変換ではありません。


# 戻り値

  * `T`: MJ2000フレームをMODフレームに整列させる回転。

# 参考文献

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.

```
