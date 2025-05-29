```
  XFuzz, Ps1, Ps2 = XFuzzEn(Sig1, Sig2)
```

`XFuzz`（クロスファジーエントロピー推定値）と、`Sig1`および`Sig2`に含まれるデータ系列に対して推定された平均ファジー距離（m:Ps1, m+1:Ps2、m = [1,2]）を返します。デフォルトのパラメータを使用します：埋め込み次元 = 2、時間遅延 = 1、ファジー関数（Fx）= 'default'、ファジー関数パラメータ（r）= [0.2, 2]、対数 = 自然対数

```
  XFuzz, Ps1, Ps2 = XFuzzEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, r::Union{Real,Tuple{Real,Real}}=(.2,2), Fx::String="default", Logx::Real=exp(1))
```

`Sig1`および`Sig2`のデータ系列に対して、指定された'キーワード'引数を使用して、次元 = [1,...,m]のクロスファジーエントロピー推定値（`XFuzz`）を返します。

# 引数:

`m`     - 埋め込み次元、正の整数   [デフォルト: 2]    

`tau`   - 時間遅延、正の整数            [デフォルト: 1]    

`Fx`    - ファジー関数名、次のいずれか:              {`"sigmoid", "modsampen", "default", "gudermannian",`             `"bell", "triangular", "trapezoidal1", "trapezoidal2",`             `"z_shaped", "gaussian", "constgaussian"`}

`r`     - ファジー関数パラメータ、正の値のスカラーまたは2要素のタプル。各ファジー関数の`r`パラメータは次のように定義されます：

```
        sigmoid:        r(1) = 指数引数の除数
                        r(2) = 引数から引かれる値（除算前）
        modsampen:      r(1) = 指数引数の除数
                        r(2) = 引数から引かれる値（除算前）
        default:        r(1) = 指数引数の除数
                        r(2) = 引数の指数（除算前）
        gudermannian:   r    = gudermannian関数への引数の分子の値を持つスカラー：
                              GD(x) = atan(tanh(`r`/x)).
        triangular:     r = 三角関数の閾値（コーナーポイント）を持つスカラー。
        trapezoidal1:   r = 台形の上（2r）および下（r）コーナーポイントに対応する値を持つスカラー。
        trapezoidal2:   r(1) = 台形の上コーナーポイントに対応する値。
                        r(2) = 台形の下コーナーポイントに対応する値。
        z_shaped:       r = z形の上（2r）および下（r）コーナーポイントに対応する値を持つスカラー。
        bell:           r(1) = 距離値の除数
                        r(2) = 一般化されたベル型関数の指数
        gaussian:       r = ガウス曲線の傾きをスケールする値を持つスカラー。
        constgaussian:  r = ガウス曲線の下限閾値と形状を定義する値を持つスカラー。                    
        [非推奨] linear:       r  = 整数値。r = 0のとき、指数関数の引数は
                              [0 1]の間で正規化されます。r = 1のとき、
                              指数引数の最小値は0に設定されます。
```

`Logx`  - 対数の底、正のスカラー  

'キーワード'引数に関する詳細情報については、EntropyHubガイドを参照してください。

# 参照: `FuzzEn`, `XSampEn`, `XApEn`, `FuzzEn2D`, `XMSEn`, `MSEn`

# 参考文献:

```
  [1] Hong-Bo Xie, et al.,
      "Cross-fuzzy entropy: A new method to test pattern synchrony of
      bivariate time series." 
      Information Sciences 
      180.9 (2010): 1715-1724.

  [3] Hamed Azami, et al.
      "Fuzzy Entropy Metrics for the Analysis of Biomedical Signals: 
      Assessment and Comparison"
      IEEE Access
      7 (2019): 104833-104847
```
