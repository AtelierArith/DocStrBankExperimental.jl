```
Dist, Ppi = DistEn(Sig)
```

データシーケンス（`Sig`）から推定された分布エントロピー推定値（`Dist`）と対応する分布確率（`Ppi`）を返します。デフォルトのパラメータを使用します：埋め込み次元 = 2、時間遅延 = 1、ビンニング方法 = 'Sturges'、対数 = 基数2、正規化 = ヒストグラムビンの数に対して

```
Dist, Ppi = DistEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, Bins::Union{Int,String}="Sturges", Logx::Real=2, Norm::Bool=true)
```

指定された「キーワード」引数を使用して、データシーケンス（`Sig`）から推定された分布エントロピー推定値（`Dist`）を返します：

# 引数：

`m`     - 埋め込み次元、正の整数  

`tau`   - 時間遅延、正の整数  

`Bins`  - 距離分布のヒストグラムビン選択方法、次のいずれか：  

```
      ビンの数を示す1より大きい整数、または次の文字列のいずれか 
      {'sturges','sqrt','rice','doanes'}
      [デフォルト: 'sturges']
```

`Logx`  - 対数の基数、正のスカラー（自然対数の場合は0を入力）   

`Norm`  - DistEn値の正規化：  

```
      [false]  正規化なし。
      [true]   ヒストグラムビンの数に対して正規化 - デフォルト
```

# 参照： `XDistEn`, `DistEn2D`, `MSEn`, `K2En`

# 参考文献：

```
[1] Li, Peng, et al.,
    "Assessing the complexity of short-term heartbeat interval 
    series by distribution entropy." 
    Medical & biological engineering & computing 
    53.1 (2015): 77-87.
```
