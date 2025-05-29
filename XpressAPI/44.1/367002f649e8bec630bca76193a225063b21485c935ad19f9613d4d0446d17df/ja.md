```
XPRSnlpvalidatekkt(prob, mode, respectbasis, updatemult, violtarget)::prob
```

最適性条件の第一条件、すなわちカラッシュ-クーン-タッカー（KKT）条件を現在の解に対して検証します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `mode::Integer`: 計算モードは次のように設定できます: 0現在の双対解を使用して現在の解で削減コストを再計算します。
  * `respectbasis::Integer`: 制約がアクティブかどうかを評価するために定義された方法は次の通りです: 0再計算されたスラック活動をXSLP*ECFTOL*Rと比較します。
  * `updatemult::Integer`: 計算された値は次のように設定できます: 0XSLP*VALIDATIONINDEX*K測定を計算するためのみに使用されます。
  * `violtarget::Float64`: 最良のKKT乗数を計算する際に、削減コストの違反の均等分布を強制するために、それらに制約を課すことが可能です。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSnlpvalidatekkt](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpvalidatekkt.html)のドキュメントも参照してください。
