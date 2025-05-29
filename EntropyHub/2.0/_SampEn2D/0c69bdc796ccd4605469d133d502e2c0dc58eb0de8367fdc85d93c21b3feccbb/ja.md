```
SE2D, Phi1, Phi2 = SampEn2D(Mat)
```

データ行列（`Mat`）に対してデフォルトのパラメータを使用して推定された二次元サンプルエントロピー推定値（`SE2D`）と一致したサブマトリックスの数（m:Phi1, m+1:Phi2）を返します：時間遅延 = 1、半径距離閾値 = 0.2*SD（`Mat`）、対数 = 自然、マトリックステンプレートサイズ = [floor(H/10) floor(W/10)]（ここでHとWはデータ行列`Mat`の高さ（行）と幅（列）を表します）

** Matの最小次元サイズは> 10でなければなりません。**

```
SE2D, Phi1, Phi2 = SampEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10),             
                                tau::Int=1, r::Real=0.2*std(Mat,corrected=false), Logx::Real=exp(1), Lock::Bool=true)
```

指定された「キーワード」引数を使用してデータ行列（`Mat`）に対して二次元サンプルエントロピー（`SE2D`）推定値を返します：

# 引数：

`m`     - テンプレートサブマトリックスの次元、整数スカラー（すなわち、同じ高さと幅）または最小値が> 1の整数の二要素ベクトル[高さ、幅]（デフォルト：[floor(H/10) floor(W/10)]）

`tau`   - 時間遅延、正の整数（デフォルト：1）

`r`     - 距離閾値、正のスカラー（デフォルト：0.2*SD(Mat)）

`Logx`  - 対数の底、正のスカラー（デフォルト：自然）

`Lock`  - デフォルトでは、SampEn2Dはメモリエラーを防ぐために最大サイズ128 x 128の行列のみを許可します。例：Mat = [200 x 200]、m = 3、tau = 1の場合、SampEn2Dは753049836要素のベクトルを作成します。[128 x 128]要素を超える行列を有効にするには、`Lock`をfalseに設定します。（デフォルト：true）

```
      `WARNING: 許可された行列サイズのロックを解除すると、Julia
      IDEがクラッシュする可能性があります。`
```

# 参照：`SampEn`、`FuzzEn2D`、`XSampEn`、`MSEn`

# 参考文献：

```
[1] Luiz Eduardo Virgili Silva, et al.,
     "二次元サンプルエントロピー：不規則性を通じて画像テクスチャを評価する。"
     Biomedical Physics & Engineering Express
     2.4 (2016): 045002.
```
