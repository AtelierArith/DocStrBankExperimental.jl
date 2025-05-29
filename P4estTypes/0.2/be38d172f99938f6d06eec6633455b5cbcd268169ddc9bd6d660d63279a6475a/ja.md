```
iterateforest(forest; kw...)
```

ランクローカルフォレストのすべてのボリューム、フェイス、エッジ、およびコーナーに対して、キーワード引数として渡されたコールバックを実行します。

イテレーションのためのキーワード引数（`kw...`）は次のとおりです：

  * `ghost = nothing`: メッシュに関連付けられたゴーストレイヤー。隣接要素（ランクローカルでない）に対する`face`、`edge`、および`corner`コールバックで使用されます。
  * `volume = nothing`: ローカルフォレストのすべてのボリューム（別名クアドラント）に対して使用されるコールバックで、プロトタイプは`volume(forest, ghost, quadrant, quadid, treeid, userdata)`です。
  * `face = nothing`: まだ実装されていません。
  * `edge = nothing`: まだ実装されていません。
  * `corner = nothing`: まだ実装されていません。
  * `userdata = nothing`: コールバックに渡されるユーザーデータです。

イテレーションに関する詳細については、`@doc P4estTypes.P4est.p4est_iterate`および`@doc P4estTypes.P4est.p8est_iterate`を参照してください。
