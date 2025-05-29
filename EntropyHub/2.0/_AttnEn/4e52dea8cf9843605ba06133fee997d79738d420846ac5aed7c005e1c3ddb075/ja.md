```
  Av4, (Hxx,Hnn,Hxn,Hnx) = AttnEn(Sig)
```

データシーケンス（`Sig`）から推定されたサブエントロピー（`Hxx`,`Hxn`,`Hnn`,`Hnx`）の平均として計算された注意エントロピー（`Av4`）を返します。底は2の対数を使用します。

```
  Av4, (Hxx, Hnn, Hxn, Hnx) = AttnEn(Sig::AbstractArray{T,1} where T<:Real; Logx::Real=2)
```

データシーケンス（`Sig`）から注意エントロピー（`Av4`）とサブエントロピー（`Hxx`,`Hnn`,`Hxn`,`Hnx`）を返します。ここで、   Hxx:    ローカルマキシマ間隔のエントロピー   Hnn:    ローカルミニマ間隔のエントロピー   Hxn:    ローカルマキシマとその後のミニマ間の間隔のエントロピー   Hnx:    ローカルミニマとその後のマキシマ間の間隔のエントロピー  

# 引数:

`Logx`  - 対数の底、正のスカラー               （自然対数の場合は0を入力）

`EnofEn`、`SpecEn`、`XSpecEn`、`PermEn`、`MSEn`も参照してください。

# 参考文献:

```
  [1] Jiawei Yang, et al.,
      "Classification of Interbeat Interval Time-series Using 
      Attention Entropy." 
      IEEE Transactions on Affective Computing 
      (2020)
```
