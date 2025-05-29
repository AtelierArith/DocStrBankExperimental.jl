```
fmi3GetContinuousStates(c::FMU3Instance)
```

新しい（連続）状態ベクトル x を返します

# 引数

  * `c::FMU3Instance`: FMI 2.0.2 標準におけるインスタンス化された FMU を表す可変構造体。

# 戻り値

  * `x::Array{fmi3Float64}`: 新しい連続状態ベクトル `x` を表す `fmi3Float64` 値の配列を返します。

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 2.3.3. 状態: 初期化モード

他の情報は [`fmi3GetContinuousStates`](@ref) を参照してください。
