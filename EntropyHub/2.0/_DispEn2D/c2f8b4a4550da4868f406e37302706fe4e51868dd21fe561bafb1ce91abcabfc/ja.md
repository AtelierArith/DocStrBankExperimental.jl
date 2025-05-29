```
Disp2D, RDE = DispEn2D(Mat)
```

データ行列（`Mat`）に対して、二次元分散エントロピー推定値（`Disp2D`）と逆二次元分散エントロピー（`RDE`）をデフォルトのパラメータを使用して返します：時間遅延 = 1、シンボル = 3、対数 = 自然、データ変換 = 正規化累積分布関数（`'ncdf'`）、対数 = 自然、テンプレート行列サイズ = [floor(H/10) floor(W/10)]（ここで、HとWはデータ行列`Mat`の高さ（行）と幅（列）を表します）

** Matの行と列の最小数は> 10でなければなりません。**

```
Disp2D, RDE = DispEn2D(Mat::AbstractArray{T,2} where T<:Real; 
                    m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10), tau::Int=1,
                        c::Int=3, Typex::String="ncdf", Logx::Real=exp(1), Norm::Bool=false, Lock::Bool=true)
```

データ行列（`Mat`）に対して、指定された'キーワード'引数を使用して二次元分散エントロピー（`Disp2D`）と逆二次元分布エントロピー（`RDE`）の推定値を返します：

# 引数：

`m`     - テンプレートサブマトリックスの次元、整数スカラー（すなわち、同じ高さと幅）または整数の二要素タプル [高さ、幅] で、最小値 > 1。           [デフォルト: [floor(H/10) floor(W/10)]]

`tau`   - 時間遅延、正の整数       [デフォルト: 1]  

`c`     - シンボルの数、整数 > 1 `Typex` - シンボリックマッピング変換のタイプ、次のいずれか：           {`linear`, `kmeans`, `ncdf`, `equal`}           これらの変換に関する詳細は`EntropyHub Guide`を参照してください。     `Logx`  - 対数の底、正のスカラー        [デフォルト: 自然]

```
      ** 自然対数の場合は0を入力してください。**
```

`Norm`  - `Disp2D`値の正規化、ブール値：             - [false]   正規化なし - デフォルト             - [true]    可能な分散パターンの数に対して正規化します。     `Lock`  - デフォルトでは、DispEn2Dは最大サイズ128 x 128の行列のみを許可し、RAMにデータを保存する際のメモリエラーを防ぎます。            例：Mat = [200 x 200]、m = 3、tau = 1の場合、DispEn2D            は753049836要素のベクトルを作成します。[128 x 128]要素を超える行列を有効にするには、`Lock`をfalseに設定します。           [デフォルト: 'true']           `警告: 許可された行列サイズのロックを解除すると、Julia IDEがクラッシュする可能性があります。`

# 参照：`DispEn`、`DistEn2D`、`SampEn2D`、`FuzzEn2D`、`MSEn`

# 参考文献：

```
[1] Hamed Azami, et al.,
    "Two-dimensional dispersion entropy: An information-theoretic 
    method for irregularity analysis of images."
    Signal Processing: Image Communication, 
    75 (2019): 178-187.
```
