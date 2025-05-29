```
  Fuzz, Ps1, Ps2 = FuzzEn(Sig)
```

データ系列 `Sig` から推定されたファジーエントロピー推定値 `Fuzz` と平均ファジー距離 (`m`:Ps1, `m+1`:Ps2) を返します。デフォルトのパラメータを使用します：埋め込み次元 = 2、時間遅延 = 1、ファジー関数 (`Fx`) = "default"、ファジー関数パラメータ (`r`) = [0.2, 2]、対数 = 自然対数

```
  Fuzz, Ps1, Ps2 = FuzzEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Union{Real,Tuple{Real,Real}}=(.2,2), Fx::String="default", Logx::Real=exp(1))
```

指定されたキーワード引数を使用して、データ系列 `Sig` に対して次元 = [1,...,`m`] のファジーエントロピー推定値 `Fuzz` を返します：

# 引数：

`m`     - 埋め込み次元、正の整数  [デフォルト: 2]

`tau`   - 時間遅延、正の整数        [デフォルト: 1]

`Fx`    - ファジー関数名、次のいずれか：              {`"sigmoid", "modsampen", "default", "gudermannian",`             `"bell", "triangular", "trapezoidal1", "trapezoidal2",`             `"z_shaped", "gaussian", "constgaussian"`}

`r`     - ファジー関数パラメータ、1要素のスカラーまたは正の値の2要素タプル。各ファジー関数の `r` パラメータは次のように定義されます：      [デフォルト: [.2 2]]

```
          default:        r(1) = 指数関数の引数の除数
                          r(2) = 引数の指数（前割り算）
          sigmoid:        r(1) = 指数関数の引数の除数
                          r(2) = 引数から引かれる値（前割り算）
          modsampen:      r(1) = 指数関数の引数の除数
                          r(2) = 引数から引かれる値（前割り算）
          gudermannian:   r  = スカラーで、その値はgudermannian関数への引数の分子：
                              GD(x) = atan(tanh(`r`/x))
          triangular:     r = スカラーで、その値は三角関数の閾値（コーナーポイント）。
          trapezoidal1:   r = スカラーで、その値は台形の上（2r）および下（r）コーナーポイントに対応。
          trapezoidal2:   r(1) = 台形の上コーナーポイントに対応する値。
                          r(2) = 台形の下コーナーポイントに対応する値。
          z_shaped:       r = スカラーで、その値はz字型の上（2r）および下（r）コーナーポイントに対応。
          bell:           r(1) = 距離値の除数
                          r(2) = 一般化されたベル型関数の指数
          gaussian:       r = スカラーで、その値はガウス曲線の傾きをスケーリングします。
          constgaussian:  r = スカラーで、その値はガウス曲線の下限と形状を定義します。                    
          [非推奨] linear:       r  = 整数値。r = 0 の場合、指数関数の引数は 
                              [0 1] の間で正規化されます。r = 1 の場合、
                              指数関数の引数の最小値は0に設定されます。
```

`Logx`  - 対数の底、正のスカラー  [デフォルト: 自然]

## キーワード引数に関する詳細情報は、EntropyHubガイドを参照してください。

# 参照： `SampEn`, `ApEn`, `PermEn`, `DispEn`, `XFuzzEn`, `FuzzEn2D`, `MSEn`

# 参考文献：

```
  [1] Weiting Chen, et al.
      "ファジーエントロピーに基づく表面EMG信号の特性化."
      IEEE Transactions on neural systems and rehabilitation engineering
      15.2 (2007): 266-272.

  [2] Hong-Bo Xie, Wei-Xing He, and Hui Liu
      "非線形類似性に基づくサンプルエントロピーを用いた時系列の規則性の測定."
      Physics Letters A
      372.48 (2008): 7140-7146.

  [3] Hamed Azami, et al.
      "生体信号の分析のためのファジーエントロピー指標： 
      評価と比較"
      IEEE Access
      7 (2019): 104833-104847
```
