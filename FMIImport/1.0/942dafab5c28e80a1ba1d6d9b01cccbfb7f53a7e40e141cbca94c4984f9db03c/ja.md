```
fmi3GetNominalsOfContinuousStates(c::FMU3Instance)
```

連続状態の名目値を返します。

# 引数

  * `c::FMU3Instance`: FMI 2.0.2 標準におけるインスタンス化された FMU を表す可変構造体。

# 戻り値

  * `x::Array{fmi3Float64}`: 連続状態ベクトル `x` の新しい名目値を表す `fmi3Float64` 値の配列を返します。

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存定義
  * FMISpec3.0: 2.3.3. 状態: 初期化モード

他の情報は [`fmi3GetNominalsOfContinuousStates`](@ref) を参照してください。
