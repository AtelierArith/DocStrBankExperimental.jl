```
DemoSystems
```

制御文献からの標準テストシステムを含むモジュールです。

返されるシステムは `StateSpace` または `DelayLTISystem` のタイプです。

デフォルトのパラメータはキーワード引数を使用して変更できます。

# SISOシステム

  * `DemoSystems.lag(;T=1)`     一次システム  `1/(sT+1)`
  * `DemoSystems.fotd(;T=1, τ=1)`   時間遅延を持つ一次システム `exp(-sτ)/(sT+1)`
  * `DemoSystems.sotd(;T=1, T2=10, τ=1)`   時間遅延を持つ二次非共鳴システム `exp(-sτ)/(sT+1)/(sT2 + 1)`
  * `DemoSystems.resonant(;ω0=1, ζ=0.25)`   二次共鳴システム `ω0^2/(s^2 + 2ζ*ω0*s + ω0^2)`
  * `DemoSystems.double_mass_model` 柔軟な伝達の四次モデル。詳細についてはドキュメント文字列を参照してください。

# MIMOシステム

  * `DemoSystems.woodberry()`     ウッド・ベリー蒸留塔
  * `DemoSystems.doylesat(;a=10)`    ドイルによる回転体の例

詳細については、特定のシステムのヘルプを参照してください。
