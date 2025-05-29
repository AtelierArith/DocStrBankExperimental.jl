```
  Cond, SEw, SEz = CondEn(Sig)
```

データシーケンス（`Sig`）から推定された修正された条件エントロピー推定値（`Cond`）と対応するシャノンエントロピー（m: `SEw`, m+1: `SEz`）を返します。デフォルトのパラメータを使用します：埋め込み次元 = 2、時間遅延 = 1、シンボル = 6、対数 = 自然、正規化 = false *注：CondEn(m=1)は`Sig`のシャノンエントロピーを返します。*

```
  Cond, SEw, SEz = CondEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, c::Int=6, Logx::Real=exp(1), Norm::Bool=false)
```

指定された「キーワード」引数を使用して、データシーケンス（`Sig`）から修正された条件エントロピー推定値（`Cond`）を返します：

# 引数：

`m`     - 埋め込み次元、1より大きい整数  

`tau`   - 時間遅延、正の整数  

`c`     - シンボルの数、1より大きい整数  

`Logx`  - 対数の底、正のスカラー  

`Norm`  - CondEn値の正規化：  

```
        [false]  正規化なし - デフォルト
        [true]   データシーケンス`Sig`のシャノンエントロピーに対して正規化
```

# 参照：`XCondEn`、`MSEn`、`PermEn`、`DistEn`、`XPermEn`

# 参考文献：

```
  [1] Alberto Porta, et al.,
      "Measuring regularity by means of a corrected conditional
      entropy in sympathetic outflow." 
      Biological cybernetics 
      78.1 (1998): 71-78.
```
