```
Slop = SlopEn(Sig)
```

データ系列（`Sig`）の埋め込み次元 [2, ..., m] に対するスロープエントロピー（`Slop`）の推定値を、デフォルトのパラメータを使用して返します：埋め込み次元 = 2、時間遅延 = 1、角度の閾値 = [5 45]、対数 = 基数 2 

```
Slop = SlopEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, Lvls::AbstractArray{T,1} where T<:Real=[5, 45], Logx::Real=2, Norm::Bool=true)
```

指定された「キーワード」引数を使用して、データ系列（`Sig`）のスロープエントロピー（`Slop`）の推定値を返します：

# 引数：

`m`     - 埋め込み次元、1より大きい整数   	

```
      SlopEnは各次元 [2,...,m] の推定値を返します
```

`tau`   - 時間遅延、正の整数    

`Lvls`  - 角度の閾値、範囲 [0 90] 度の単調増加する値のベクトル。

`Logx`  - 対数の基数、正のスカラー（自然対数の場合は0を入力）   

`Norm`  - SlopEn値の正規化、ブール演算子： 

```
      [false]  正規化なし
      [true]   見つかったパターンの数に対して正規化（デフォルト）
```

# 参照： `PhasEn`, `GridEn`, `MSEn`, `CoSiEn`, `SampEn`, `ApEn`

# 参考文献：

```
[1] David Cuesta-Frau,
    "Slope Entropy: A New Time Series Complexity Estimator Based on
    Both Symbolic Patterns and Amplitude Information." 
    Entropy 
    21.12 (2019): 1167.
```
