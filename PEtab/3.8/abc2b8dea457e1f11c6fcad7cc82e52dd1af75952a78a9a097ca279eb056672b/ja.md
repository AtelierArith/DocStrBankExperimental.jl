```
to_chains(res, target::PEtabLogDensity; kwargs...)::MCMCChains
```

`PEtabLogDensity`を用いて得られたベイズ推論の結果を`MCMCChains`に変換します。

`res`はAdvancedHMC.jlまたはAdaptiveMCMC.jlからの推論結果である可能性があります。返されるチェーンは、事前スケールでのパラメータを持っています。

# キーワード引数

  * `start_time`: 推論のためのオプションの開始時間で、`now()`を使用して取得します。
  * `end_time`: 推論のためのオプションの終了時間で、`now()`を使用して取得します。

!!! note
    この関数を使用するには、MCMCChainsパッケージをロードする必要があります: `using MCMCChains`

