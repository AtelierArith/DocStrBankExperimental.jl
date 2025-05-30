```
Curve(x:: AbstractVector, y:: AbstractVector; method=ItpLinear(), extrapolation=EtpFlat(), logx=false, logy=false, sort=true)
```

標準的な曲線コンストラクタ。曲線インスタンスの補間/外挿オブジェクトを作成します。ポイント `x` と `y` はソートされている必要はなく、これはCurveコンストラクタ内で行われます。

補間/外挿の詳細はキーワード引数を使用して変更でき、デフォルトは次のとおりです：

  * 線形補間
  * 定数外挿
  * 対数軸なし

メソッド ˋGridded(x)ˋ は、xグリッドが非一様であることができるように使用する必要があります。

ˋmethodˋ の有効な選択肢は次のとおりです：

  * ˋItpLinear()ˋ、Interpolation.jl の ˋGridded(Linear())ˋ に対応 - デフォルト
  * ˋItpConstant()ˋ、Interpolation.jl の ˋGridded(Constant())ˋ に対応

ˋextrapolationˋ の有効な選択肢は次のとおりです：

  * ˋEtpFlat()ˋ、Interpolation.jl の ˋFlat()ˋ に対応 - デフォルト
  * ˋEtpLine()ˋ、Interpolation.jl の ˋLine()ˋ に対応

曲線が単一のポイントのみで構成されている場合、常に定数外挿が使用されます。

  * `sort=true`: デフォルトでは、入力ポイントはソートされ、重複するx値は削除されます。`sort=true` は安全ではなく、ポイントがソートされていて重複していないことが保証されるCurves.jlの内部操作のみに使用されることを意図しています。
