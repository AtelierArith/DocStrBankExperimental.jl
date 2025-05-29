```
duration(keyrate::KeyRateDuration,curve,cashflows)    
duration(keyrate::KeyRateDuration,curve,cashflows,timepoints)
duration(keyrate::KeyRateDuration,curve,cashflows,timepoints,krd_points)
```

**ゼロ**（パではなく）曲線を、KeyRateDuration(time)で指定された時点で`shift`というキーワード引数でシフトさせることによって、キー レート デュレーションを計算します。

アプローチは、曲線を`krd_points`（デフォルトは`1`からキャッシュフローの最後の時点までの単位ステップ）に分割することです。`KeyRateDuration`内の時点に対応するゼロレートは、`shift`（`KeyRateZero`または`KeyRatePar`コンストラクタで指定）によってシフトされます。シフトされたレートから新しい曲線が作成されます。これは、シフトされたセクションの「幅」が±1期間であることを意味します。特定のポイントが`krd_points`を介して指定されていない限り。

`curve`は、任意のFinanceModels.jl曲線である可能性があります（例：`FinanceModels.Zero(...)`を介して構築された曲線である必要はありません）。

!!! 実験的: 文献に例が少ないため、この機能にはJuliaActuaryの他の機能のような単体テストがありません。さらに、APIは将来のメジャー/マイナー バージョンの更新で変更される可能性があります。

# 例

```julia-repl
julia> riskfree_maturities = [0.5, 1.0, 1.5, 2.0];

julia> riskfree    = [0.05, 0.058, 0.064,0.068];

julia> rf_curve = FinanceModels.Zero(riskfree,riskfree_maturities);

julia> cfs = [10,10,10,10,10];

julia> duration(KeyRate(1),rf_curve,cfs)
8.932800152336995

```

# 拡張ヘルプ

キー レート デュレーションは、文献や実務において明確に定義されたトピックではありません。以下の参考文献は、パ曲線をショックさせることが実務でより一般的であることを示唆していますが、ゼロ曲線はより一貫した結果を生み出します。将来のバージョンでは、パ曲線のシフトをサポートする可能性があります。

参考文献:

  * [Quant Finance Stack Exchange: To compute key rate duration, shall I use par curve or zero curve?](https://quant.stackexchange.com/questions/33891/to-compute-key-rate-duration-shall-i-use-par-curve-or-zero-curve)
  * (Financial Exam Help 123](http://www.financialexamhelp123.com/key-rate-duration/)
