```
Data( 
    e                   :: GrumpsEstimator,
    ss                  :: Sources,
    v                   :: Variables,
    microintegrator     :: MicroIntegrator = DefaultMicroIntegrator(),
    macrointegrator     :: MacroIntegrator = DefaultMacroIntegrator(),
    T                   :: Type = F64,
    options             :: DataOptions = GrumpsDataOptions(),
    replicable          :: Bool = true
    )
```

ユーザー入力を受け取り、それをGrumpsが理解できるオブジェクトに変換します。これはGrumpsData(...)と同義です。

*Data*は以下の引数を受け取ります。最初の3つは必須です：

  * *e*:                   推定器; [Estimator choice](@ref)を参照
  * *ss*:                  データソース; [Data entry](@ref)を参照
  * *v*:                   使用する変数; [Data entry](@ref)を参照
  * *o*:                   使用する最適化オプション
  * *microintegrator*:     マイクロインテグレーター; [Choice of integration method (integrators)](@ref)を参照
  * *macrointegrator*:     マクロインテグレーター; [Choice of integration method (integrators)](@ref)を参照
  * *T*:                   浮動小数点型; あまりテストされていない
  * *u*:                   まだ実装されていない
  * *options*:             使用するデータオプション; [Data storage options](@ref)を参照
  * *replicable*:          結果が再現可能であるべきかどうか（trueに設定するとデータ作成の速度が遅くなります）
