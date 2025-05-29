```
r_mj2000_to_gcrf_iau2006([T, ]jd_tt::Number = 0) -> T
```

J2000平均赤道フレームを地心天体基準フレーム（GCRF）に整列させる回転を計算します。このアルゴリズムはIAU-2006理論を使用しています。この回転は日付に依存しないバイアスマトリックスであることに注意してください。ただし、この関数はAPIの互換性を保つために引数`jd_tt`を受け取ります。

回転のタイプはオプションの変数`T`によって説明されます。`DCM`の場合、DCMが返されます。それ以外の場合、`Quaternion`の場合はQuaternionが返されます。このパラメータが省略された場合、`DCM`にフォールバックします。

!!! info
    **[1]** によると、MJ2000 <=> GCRFを変換するフレームバイアスは、すべての時刻に対して正確な変換ではありません。


# Returns

  * `T`: MJ2000フレームをMODフレームに整列させる回転。

# References

  * **[1]**: Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.

```
