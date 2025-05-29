```
  XDist, Ppi = XDistEn(Sig1, Sig2)
```

`XDist`（クロス分布エントロピー推定値）と、`Sig1`と`Sig2`に含まれるデータシーケンス間で推定された対応する分布確率（`Ppi`）を返します。デフォルトのパラメータを使用します：埋め込み次元 = 2、時間遅延 = 1、ビンニング方法 = 'Sturges'、対数 = 基数2、正規化 = ヒストグラムビンの数に対して。

```
  XDist, Ppi = XDistEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, Bins::Union{Int,String}="Sturges", Logx::Real=2, Norm::Bool=true)
```

`Sig1`と`Sig2`に含まれるデータシーケンス間で推定されたクロス分布エントロピー推定値（`XDist`）を返します。指定された'キーワード' = 引数を使用します：

# 引数：

`m`     - 埋め込み次元、正の整数   [デフォルト: 2]    

`tau`   - 時間遅延、正の整数            [デフォルト: 1]    

`Bins`  - 距離分布のヒストグラムビン選択方法、              1より大きい整数（ビンの数を示す）または次の文字列のいずれか{'sturges','sqrt','rice','doanes'}             [デフォルト: 'sturges'] 

`Logx`  - 対数の基数、正のスカラー         [デフォルト: 2]                 ** 自然対数の場合は0を入力してください**

`Norm`  - DistEn値の正規化：             [false]  正規化なし。             [true]   ヒストグラムビンの数に対して正規化 [デフォルト] 

# 参照：`XSampEn`、`XApEn`、`XPermEn`、`XCondEn`、`DistEn`、`DistEn2D`、`XMSEn`

# 参考文献：

```
  [1] Yuanyuan Wang and Pengjian Shang,
      "Analysis of financial stock markets through the multiscale
      cross-distribution entropy based on the Tsallis entropy."
      Nonlinear Dynamics 
      94.2 (2018): 1361-1376.
```
