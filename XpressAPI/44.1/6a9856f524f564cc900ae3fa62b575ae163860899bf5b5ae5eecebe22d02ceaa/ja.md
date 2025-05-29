```
XPRSrefinemipsol(prob, options, flags, solution, refined)::refined, status
```

**非推奨**REFINEOPSを使用してください。

MIPソリューションリファイナーを実行します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `options::Integer`: リファイメントオプション: 0MIPの分数性を減少させることが優先されます（REFINEOPSのビット10が設定されている場合、失敗した場合は他のモードに切り替えます）。
  * `flags::Union{Nothing,AbstractString}`: リファイメント中の最適化呼び出しに渡されるフラグ。
  * `solution::AbstractVector{Number}`: リファインするMIPソリューション。
  * `refined::Union{XPRSallocatable,AbstractVector{Float64}}`: 成功した場合のリファインされたMIPソリューション。この引数には`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を割り当てることができます。

# 戻り値

  * `refined::AbstractVector{Float64}`: 成功した場合のリファインされたMIPソリューション
  * `status::Int32`: リファイメント結果: 0エラーが発生しました 1ソリューションがリファインされました 2現在のソリューションがターゲット基準を満たしています 3ソリューションをリファインできません 5ソリューションがリファインされましたが、MIPの分数性を減少させることができませんでした。

C APIの対応する関数[XPRSrefinemipsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSrefinemipsol.html)のドキュメントも参照してください。
