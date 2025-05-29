```
XCond, SEw, SEz = XCondEn(Sig1, Sig2)
```

修正された交差条件エントロピー推定値（`XCond`）と対応するシャノンエントロピー（m: SEw, m+1: SEz）を返します。これは、デフォルトのパラメータを使用して`Sig1`と`Sig2`に含まれるデータシーケンスに対して推定されます：埋め込み次元 = 2、時間遅延 = 1、シンボルの数 = 6、対数 = 自然 ** 注：XCondEnは方向依存です。したがって、データシーケンス`Sig1`と`Sig2`の順序が重要です。もし`Sig1`がシーケンス'y'で、`Sig2`が2番目のシーケンス'u'である場合、`XCond`はパターンu(i)が見つかったときのy(i)が持つ情報量です。**

```
XCond, SEw, SEz = XCondEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, c::Int=6, Logx::Real=exp(1), Norm::Bool=false)
```

指定された「キーワード」引数を使用して、`Sig1`と`Sig2`に含まれるデータシーケンスの修正された交差条件エントロピー推定値（`XCond`）を返します：

# 引数：

`m`     - 埋め込み次元、1より大きい整数        [デフォルト: 2]  

`tau`   - 時間遅延、正の整数             [デフォルト: 1]  

`c`     - シンボルの数、1より大きい整数          [デフォルト: 6]  

`Logx`  - 対数の底、正のスカラー          [デフォルト: 自然] 

`Norm`  - `XCond`値の正規化：              [false]  正規化なし                  [デフォルト]

```
        [true]   交差シャノンエントロピーに対して正規化します。
```

# 参照： `XFuzzEn`, `XSampEn`, `XApEn`, `XPermEn`, `CondEn`, `XMSEn`

# 参考文献：

```
[1] Alberto Porta, et al.,
    "Conditional entropy approach for the evaluation of the 
    coupling strength." 
    Biological cybernetics 
    81.2 (1999): 119-129.
```
