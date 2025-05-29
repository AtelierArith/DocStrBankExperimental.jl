```
Dist2D = DistEn2D(Mat)
```

データ行列（`Mat`）に対して、デフォルトのパラメータを使用して推定された二次元分布エントロピー推定値（`Dist2D`）を返します：時間遅延 = 1、ヒストグラムビンニング方法 = "sturges"、対数 = 自然、テンプレート行列サイズ = [floor(H/10) floor(W/10)]（ここで、HとWはデータ行列`Mat`の高さ（行）と幅（列）を表します）

** Matの行と列の最小数は > 10 でなければなりません。**

```
Dist2D = DistEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10), tau::Int=1,
                    Bins::Union{Int,String}="Sturges", Logx::Real=2, Norm::Int=2, Lock::Bool=true)
```

指定された「キーワード」引数を使用して、データ行列（`Mat`）に対する二次元分布エントロピー（`Dist2D`）推定値を返します：

# 引数：

`m`     - テンプレートサブマトリックスの次元、整数スカラー（すなわち、同じ高さと幅）または整数の二要素タプル [高さ, 幅] で、最小値 > 1。           [デフォルト: [floor(H/10) floor(W/10)]] 

`tau`   - 時間遅延、正の整数       [デフォルト: 1]  

`Bins`  - 距離分布のヒストグラムビン選択方法、           ビンの数を示す整数 > 1、または次の文字列のいずれか {`"sturges", "sqrt", "rice", "doanes"`}           [デフォルト: 'sturges']  

`Logx`  - 対数の底、正のスカラー        [デフォルト: 自然]

```
      ** 自然対数の場合は0を入力してください。**
```

`Norm`  - `Dist2D`値の正規化、次の整数のいずれか：           [0]  正規化なし。           [1]  データ行列（`Mat`）の値を範囲 [0 1] に正規化。           [2]  データ行列（`Mat`）の値を範囲 [0 1] に正規化し、                分布エントロピー値（`Dist2D`）をヒストグラムビンの数に対して正規化。  [デフォルト]           [3]  データ行列の値を正規化せずに、                ヒストグラムビンの数に対して分布エントロピー値を正規化。 

`Lock`  - デフォルトでは、DistEn2Dは最大サイズ128 x 128の行列のみを許可し、RAMにデータを保存する際のメモリエラーを防ぎます。            例：Mat = [200 x 200]、m = 3、tau = 1の場合、DistEn2Dは            753049836要素のベクトルを作成します。[128 x 128]要素を超える行列を有効にするには、`Lock`をfalseに設定します。           [デフォルト: 'true']           `警告: 許可された行列サイズのロックを解除すると、Julia IDEがクラッシュする可能性があります。`

# 参照：`DistEn`、`XDistEn`、`SampEn2D`、`FuzzEn2D`、`MSEn`

# 参考文献：

```
[1] Hamed Azami, Javier Escudero and Anne Humeau-Heurtier,
    "Bidimensional distribution entropy to analyze the irregularity
    of small-sized textures."
    IEEE Signal Processing Letters 
    24.9 (2017): 1338-1342.
```
