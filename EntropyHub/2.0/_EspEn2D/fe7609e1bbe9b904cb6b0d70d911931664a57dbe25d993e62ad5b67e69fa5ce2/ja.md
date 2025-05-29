```
Esp2D,  = EspEn2D(Mat)
```

データ行列（`Mat`）に対して、デフォルトのパラメータを使用して推定された二次元エスピノサエントロピー推定値（`Esp2D`）を返します： 時間遅延 = 1、許容閾値 = 20、類似度の割合 = 0.7、対数 = 自然、行列テンプレートサイズ = [floor(H/10) floor(W/10)]、 （ここで H と W はデータ行列 `Mat` の高さ（行）と幅（列）を表します） ** `Mat` の行と列の最小数は > 10 でなければなりません。

```
Esp2D = EspEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10),             
                                tau::Int=1, r::Real=20, ps::Float=.7, Logx::Real=exp(1), Lock::Bool=true)
```

指定された「キーワード」引数を使用して、データ行列（`Mat`）に対する二次元エスピノサエントロピー（`Esp2D`）推定値を返します：

# 引数：

`m`     - テンプレートサブマトリックスの次元、整数スカラー（すなわち、同じ高さと幅）または最小値 > 1 の整数の二要素ベクトル [高さ, 幅] （デフォルト：[floor(H/10) floor(W/10)]） 

`tau`   - 時間遅延、正の整数（デフォルト：1） 

`r`     - 許容閾値、正のスカラー（デフォルト：20） 

`ps`    - 類似度の割合、範囲 [0 1] の値（デフォルト：0.7） 

`Logx`  - 対数の底、正のスカラー（デフォルト：自然）  

`Lock`  - デフォルトでは、EspEn2D はメモリエラーを防ぐために最大サイズ 128 x 128 の行列のみを許可します。例：Mat = [200 x 200]、m = 3、tau = 1 の場合、EspEn2D は 753049836 要素のベクトルを作成します。           [128 x 128] 要素を超える行列を有効にするには、`Lock` を false に設定します。（デフォルト：true）  

```
      `WARNING: unlocking the permitted matrix size may cause your Julia
      IDE to crash.`
```

# 参照： `SampEn2D`, `FuzzEn2D`, `DispEn2D`, `DistEn2D`, `PermEn2D`

# 参考文献：

```
[1] Ricardo Espinosa, et al.,
    "Two-dimensional EspEn: A New Approach to Analyze Image Texture 
    by Irregularity." 
    Entropy,
    23:1261 (2021)
```
