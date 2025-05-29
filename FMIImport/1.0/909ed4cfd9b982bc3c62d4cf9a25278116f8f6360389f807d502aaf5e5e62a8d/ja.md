```
fmi3GetContinuousStateDerivatives(c::FMU3Instance)
```

現在の時間瞬間および現在の状態における状態導関数を計算します。

# 引数

  * `c::FMU3Instance`: FMI 3.0 標準における FMU のインスタンス化されたインスタンスを表す可変構造体。

# 戻り値

  * `derivatives::Array{fmi3Float64}`: 現在の状態に対する `derivatives` を表す `fmi3Float64` 値の配列を返します。導関数ベクトルの要素の順序は状態ベクトルの順序と同じです。

# 出典

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 プラットフォーム依存の定義
  * FMISpec3.0: 3.2.1. 状態: 連続時間モード

他にも [`fmi3GetContinuousStateDerivatives`](@ref) を参照してください。
