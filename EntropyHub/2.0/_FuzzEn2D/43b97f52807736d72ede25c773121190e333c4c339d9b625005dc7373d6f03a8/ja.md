```
Fuzz2D = FuzzEn2D(Mat)
```

データ行列（`Mat`）に対して、デフォルトのパラメータを使用して推定された二次元ファジーエントロピー推定値（`Fuzz2D`）を返します：時間遅延 = 1、ファジー関数（Fx）= 'default'、ファジー関数パラメータ（r）= [0.2, 2]、対数 = 自然、テンプレート行列サイズ = [floor(H/10) floor(W/10)]（ここで、HとWはデータ行列'Mat'の高さと幅を表します）

** Matの最小次元サイズは> 10でなければなりません。**

```
Fuzz2D = FuzzEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10), 
                    tau::Int=1, r::Union{Real,Tuple{Real,Real}}=(.2*std(Mat, corrected=false),2), 
                        Fx::String="default", Logx::Real=exp(1), Lock::Bool=true)
```

指定された'キーワード'引数を使用して、データ行列（`Mat`）に対する二次元ファジーエントロピー（`Fuzz2D`）推定値を返します：

# 引数：

`m`     - テンプレートサブマトリックスの次元、整数スカラー（すなわち、同じ高さと幅）または最小値> 1の整数の2要素ベクトル [高さ、幅] （デフォルト：[floor(H/10) floor(W/10)]）

`tau`   - 時間遅延、正の整数（デフォルト：1）

`Fx`    - ファジー関数名、次のいずれか：{`"sigmoid", "modsampen", "default", "gudermannian",`           `"bell", "triangular", "trapezoidal1", "trapezoidal2",`           `"z_shaped", "gaussian", "constgaussian"`}

`r`     - ファジー関数パラメータ、1要素スカラーまたは正の値の2要素ベクトル。各ファジー関数の'r'パラメータは次のように定義されます：

```
      sigmoid:        r(1) = 指数引数の除数
                      r(2) = 引数から引かれる値（前除算）
      modsampen:      r(1) = 指数引数の除数
                      r(2) = 引数から引かれる値（前除算）
      default:        r (1) = 指数引数の除数
                      r(2) = 引数の指数（前除算）
      gudermannian:   r  = スカラーで、その値はgudermannian関数への引数の分子：
                           GD(x) = atan(tanh(r/x))
      triangular:     r = スカラーで、その値は三角関数の閾値（コーナーポイント）です。
      trapezoidal1:   r = スカラーで、その値は台形の上部（2r）および下部（r）コーナーポイントに対応します。
      trapezoidal2:   r(1) = 台形の上部コーナーポイントに対応する値。
                      r(2) = 台形の下部コーナーポイントに対応する値。
      z_shaped:       r = スカラーで、その値はz形の上部（2r）および下部（r）コーナーポイントに対応します。
      bell:           r(1) = 距離値の除数
                      r(2) = 一般化されたベル型関数の指数
      gaussian:       r = スカラーで、その値はガウス曲線の傾きをスケーリングします。
      constgaussian:  r = スカラーで、その値はガウス曲線の下限閾値と形状を定義します。                    
      [非推奨] linear:       r  = 整数値。r = 0のとき、指数関数の引数は
                        [0 1]の間で正規化されます。r = 1のとき、
                        指数引数の最小値は0に設定されます。
```

`Logx`  - 対数の底、正のスカラー（デフォルト：自然）

`Lock`  - デフォルトでは、FuzzEn2Dはメモリエラーを防ぐために、最大サイズ128 x 128の行列のみを許可します。例：Mat = [200 x 200]、m = 3、tau = 1の場合、FuzzEn2Dは753049836要素のベクトルを作成します。[128 x 128]要素を超える行列を有効にするには、`Lock`をfalseに設定します。（デフォルト：true）

```
      ` 警告：許可された行列サイズのロックを解除すると、
      Julia IDEがクラッシュする可能性があります。`
```

# 参照：`SampEn2D`、`FuzzEn`、`XFuzzEn`

# 参考文献：

```
[1] Luiz Fernando Segato Dos Santos, et al.,
    "Multidimensional and fuzzy sample entropy (SampEnMF) for
    quantifying H&E histological images of colorectal cancer."
    Computers in biology and medicine 
    103 (2018): 148-160.

[2] Mirvana Hilal and Anne Humeau-Heurtier,
    "Bidimensional fuzzy entropy: Principle analysis and biomedical
    applications."
    41st Annual International Conference of the IEEE (EMBC) Society
    2019.

[3] Hamed Azami, et al.
    "Fuzzy Entropy Metrics for the Analysis of Biomedical Signals: 
    Assessment and Comparison"
    IEEE Access
    7 (2019): 104833-104847
```
