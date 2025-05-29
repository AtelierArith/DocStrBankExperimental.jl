```
spa{T<:Number}(lossDiff::Matrix{T}, method ; kwargs...)::SPATest
spa{T<:Number}(lossDiff::Matrix{T} ; kwargs...)
```

この関数は、Hansen (2005) の「A Test for Superior Predictive Ability」で提案されたSPAテストを実装しています。

x*0をベースケースの予測、x*k (k = 1, ..., K) をKの代替予測、yを予測ターゲットとします。L(., .)を損失関数とします。spaの最初の引数は、行列であり、行列のk列目は次の操作によって作成されます：

L(x*k, y) - L(x*0, y)

予測損失が最初に来て、ベースケースの損失が2番目に来ることに注意してください。これはHansenの論文で説明されている内容とは逆です。

2番目のメソッド引数は、使用する方法論を決定します。現在、SPABootのみが利用可能であり、この入力タイプが提供される場合、キーワード引数は必要ありません。あるいは、ユーザーは2番目の引数を省略でき、その場合は任意のキーワード引数がSPABootコンストラクタに渡されます。詳細については、?SPABootを参照してください。最も関連性の高いキーワード引数は次のとおりです：     alpha=0.05 <- テストで使用する信頼水準

```
kernelfunction=KernelEpanechnikov() <- HAC分散推定器と共に使用するカーネル関数。詳細については、?hacvarianceを参照してください。

bandwidth=-1 <- HAC分散推定器のバンド幅。bandwidth <= -1 の場合、バンド幅はPolitis (2003) の「Adaptive Bandwidth Choice」を使用して推定されます。

blocklength=0.0 <- ブートストラップで使用するブロック長。0.0のデフォルトは、ブロック長がデータから最適に推定されることを意味します。これは、DependentBootstrapパッケージによって最も適切と見なされる方法（通常はPatton、Politis、およびWhite (2009) の選択手順）を使用します。

numresample=1000 <- ブートストラップ時に使用する再サンプルの数。

bootmethod=:stationary <- 使用するブートストラップ方法論で、デフォルトはPolitisとRomano (1993) の定常ブートストラップです。
```

SPAテストの出力はSPATest型です。詳細については、?SPATestを参照してください。

注意：Hansenは、現在このパッケージでサポートされていない定常ブートストラップを暗示するHAC分散推定器の使用を提案しています。ただし、一貫したHAC推定器は有効であり、多くの場合、好まれる可能性があることに注意してください。
