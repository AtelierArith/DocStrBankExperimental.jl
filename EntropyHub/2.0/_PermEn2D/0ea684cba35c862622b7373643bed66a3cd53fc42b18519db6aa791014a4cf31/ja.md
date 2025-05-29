```
   Perm2D = PermEn2D(Mat)
```

データ行列（`Mat`）に対して、デフォルトのパラメータ（時間遅延 = 1、対数 = 自然、テンプレート行列サイズ = [floor(H/10) floor(W/10)]）を使用して推定された二次元の順列エントロピー推定値（`Perm2D`）を返します。 （ここで、HとWはデータ行列`Mat`の高さ（行）と幅（列）を表します）

** Matの最小次元サイズは> 10でなければなりません。**

```
   Perm2D = PermEn2D(Mat::AbstractArray{T,2} where T<:Real; m::Union{Int,Tuple{Int,Int}}=floor.(Int, size(Mat)./10),             
                                   tau::Int=1, Norm::Bool=true, Logx::Real=exp(1), Lock::Bool=true)
```

指定された「キーワード」引数を使用して、データ行列（`Mat`）に対する二次元の順列エントロピー（`Perm2D`）推定値を返します。

# 引数:

`m`     - テンプレートサブマトリックスの次元、整数スカラー（すなわち、同じ高さと幅）または最小値> 1の整数の2要素ベクトル[高さ、幅]。 （デフォルト：[floor(H/10) floor(W/10)]）

`tau`   - 時間遅延、正の整数（デフォルト：1）

`Norm`  - 順列エントロピー推定の正規化、ブール値（デフォルト：true）

`Logx`  - 対数の底、正のスカラー（デフォルト：自然）

`Lock`  - デフォルトでは、PermEn2Dは、RAMにデータを保存する際のメモリエラーを防ぐために、最大サイズ128 x 128の行列のみを許可します。 例：Mat = [200 x 200]、m = 3、tau = 1の場合、SampEn2Dは753049836要素のベクトルを作成します。 [128 x 128]要素を超える行列を有効にするには、`Lock`をfalseに設定します。 （デフォルト：true）

```
         `WARNING: unlocking the permitted matrix size may cause your Julia
         IDE to crash.`
```

**注意** - 元の二次元順列エントロピーアルゴリズム[1][2]は、埋め込み行列の同値要素を考慮していません。 これを克服するために、`PermEn2D`はそのようなインスタンスのために最も低い共通ランクを使用します。 例えば、埋め込み行列Aがあるとします。 A = [3.4  5.5  7.3]                  |2.1  6    9.9|                  [7.3  1.1  2.1]              は通常、次のように順序パターンにマッピングされます。              [3.4  5.5  7.3  2.1  6  9.9  7.3  1.1  2.1] =>              [ 8    4    9    1   2   5    3    7    6 ]              しかし、インデックス4と9、3と7はそれぞれ同じ値、2.1と7.3を持っています。 代わりに、PermEn2Dは順序パターン              [ 8    4    4    1   2   5    3    3    6 ]              を使用し、最も低いランク（4と3）が代わりに使用されます（9と7の代わりに）。 したがって、可能な順列の数はもはや               (mx*my)！ではなく、(mx*my)^(mx*my)です。ここで、PermEn2Dの値は               最大シャノンエントロピー（Smax = log((mx*my)!)               $順列モチーフ行列に同じ値が見つからないと仮定$、[1]に示されているように正規化されます。

# `SampEn2D`、`FuzzEn2D`、`DispEn2D`、`DistEn2D`も参照してください

# 参考文献:

```
   [1] Haroldo Ribeiro et al.,
           "Complexity-Entropy Causality Plane as a Complexity Measure 
           for Two-Dimensional Patterns"
           PLoS ONE (2012), 7(8):e40689, 

   [2] Luciano Zunino and Haroldo Ribeiro,
           "Discriminating image textures with the multiscale
           two-dimensional complexity-entropy causality plane"
           Chaos, Solitons and Fractals,  91:679-688 (2016)

   [3] Matthew Flood and Bernd Grimm,
           "EntropyHub: An Open-source Toolkit for Entropic Time Series Analysis"
           PLoS ONE (2021) 16(11): e0259448.
```
