```julia
primitive type Stepsize <: Enum{Int32} 32
```

パスフォロー方式のステッピングスキームを指定するために使用される公開型。詳細については、ドキュメントの[内点セクション](@ref path-following-theory)を参照してください。

# 利用可能なオプション

  * `SHORT`:   パラメータtの定期的な更新。
  * `LONG`:   反復が近似中心条件を満たす場合、パラメータtの大きな更新。   反復xに対する更新の適用のためのラインサーチを結果として得る。
  * `ADAPTIVE`:   長いステッピングと同じですが、大きな更新のための係数は、近似中心条件を満たすのに必要なステップ数に応じて適応的に変更されます。
