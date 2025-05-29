```
 XPerm = XPermEn(Sig1, Sig2)
```

`Sig1` と `Sig2` に含まれるデータ系列の間で推定されたクロスパーミュテーションエントロピー推定値 (`XPerm`) を返します。デフォルトのパラメータを使用します：埋め込み次元 = 3、時間遅延 = 1、対数 = 基数 2、

```
 XPerm = XPermEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=3, tau::Int=1, Logx::Real=exp(1))
```

指定された「キーワード」引数を使用して、`Sig1` と `Sig2` に含まれるデータ系列の間で推定された順列エントロピー推定値 (`XPerm`) を返します：

# 引数：

`m`     - 埋め込み次元、整数 > 2   [デフォルト: 3]  

```
     **注意: 埋め込み次元 < 3 の場合、XPerm は未定義です。**
```

`tau`   - 時間遅延、正の整数        [デフォルト: 1]    

`Logx`  - 対数の基数、正のスカラー     [デフォルト: 2]              ** 自然対数の場合は 0 を入力してください。**    

# 参照： `PermEn`, `XApEn`, `XSampEn`, `XFuzzEn`, `XMSEn`

# 参考文献：

```
 [1] Wenbin Shi, Pengjian Shang, and Aijing Lin,
     "The coupling analysis of stock market indices based on 
     cross-permutation entropy."
     Nonlinear Dynamics
     79.4 (2015): 2439-2447.
```
