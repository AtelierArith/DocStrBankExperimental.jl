```
Point(Height::Real, Rho::Real)
```

`Point` ソースを構築して返します。`Point` はそれ自体でソースとして使用することも、高次元ソースの `anchor point` として使用することもできます。

  * `Height` : 検出器表面に対する点の高さ。
  * `Rho` : 検出器対称軸に対する点のオフ軸位置。

!!! note
    各検出器タイプは `height` を次のように異なる解釈を与えます:-

      * `CylDetector` の場合、点ソースの `height` は検出器の `face surface` から測定されると考えられます。
      * `BoreDetector` の場合、点ソースの `height` は `detector middle` から測定されると考えられ、+ve 値は検出器中心の上、-ve 値は下を示します。
      * `WellDetector` の場合、点ソースの `height` は検出器の `hole surface` から測定されると考えられます。

