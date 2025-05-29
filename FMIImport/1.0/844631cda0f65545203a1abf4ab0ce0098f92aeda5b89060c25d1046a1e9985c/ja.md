```
fmi2GetNominalsOfContinuousStates(c::FMU2Component)
```

新しい（連続）状態ベクトル x を返します

# 引数

  * `c::FMU2Component`: FMU 2.0.2 標準のインスタンス化されたインスタンスを表す可変構造体。

# 戻り値

  * `x::Array{fmi2Real}`: 新しい連続状態ベクトル `x` を表す `fmi2Real` 値の配列を返します。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 関数によって返されるステータス
  * FMISpec2.0.2[p.83]: 3.2.2 モデル方程式の評価

関連情報として [`fmi2GetNominalsOfContinuousStates`](@ref) を参照してください。
