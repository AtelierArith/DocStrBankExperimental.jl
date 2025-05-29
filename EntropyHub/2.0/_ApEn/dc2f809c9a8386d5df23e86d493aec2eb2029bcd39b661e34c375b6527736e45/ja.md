```
  Ap, Phi = ApEn(Sig)
```

データ系列 `Sig` から推定された近似エントロピー推定値 `Ap` と一致ベクトルの対数平均数 `Phi` を返します。デフォルトのパラメータを使用して、`m` = [0,1,2]、埋め込み次元 = 2、時間遅延 = 1、半径距離閾値 = 0.2*SD(`Sig`)、対数 = 自然対数

```
  Ap, Phi = ApEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Real=0.2*std(Sig,corrected=false), Logx::Real=exp(1))
```

指定されたキーワード引数を使用して、次元 = [0,1,...,`m`] のデータ系列 `Sig` の近似エントロピー推定値 `Ap` を返します。

# 引数:

`m`      - 埋め込み次元、正の整数

`tau`    - 時間遅延、正の整数

`r`      - 半径距離閾値、正のスカラー  

`Logx`   - 対数の底、正のスカラー

# 参照: `XApEn`, `SampEn`, `MSEn`, `FuzzEn`, `PermEn`, `CondEn`, `DispEn`

# 参考文献:

```
  [1] Steven M. Pincus, 
      "Approximate entropy as a measure of system complexity." 
      Proceedings of the National Academy of Sciences 
      88.6 (1991): 2297-2301.
```
