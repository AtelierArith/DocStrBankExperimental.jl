```
EopIau1980{T}
```

IAU 1980モデルの地球の向きパラメータ。

!!! note
    各フィールドは、ユリウス日でインデックス付けされた `AbstractInterpolation` になります。したがって、例えば2018年6月19日の地殻に対する極運動のX成分を取得したい場合、次のように使用できます：

    ```
    x[DateTime(2018, 6, 19, 0, 0, 0) |> datetime2julian]
    ```


# フィールド

  * `x, y`: 地殻に対する極運動 [arcsec]。
  * `Δut1_utc`: 回転角の不規則性 [s]。
  * `lod`: 日の長さのオフセット [ms]。
  * `δΔψ, δΔϵ`: IAU1980モデルに関連付けられた天体極オフセット [ミリアーク秒]。
  * `*_error`: コンポーネントの誤差 [コンポーネントと同じ単位]。
