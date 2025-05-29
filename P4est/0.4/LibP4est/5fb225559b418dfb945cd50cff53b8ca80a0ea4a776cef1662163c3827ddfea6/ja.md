```
p8est_search_partition(p4est_, call_post, quadrant_fn, point_fn, points)
```

グローバルパーティションを上から下へトラバースします。すべてのプロセッサで同様にパーティションを上から下へ進みますが、2つのユーザー提供のコールバックの結果は異なります。再帰は、複数のプロセッサ間で分割されたブランチにのみ進みます。コールバック関数は、分割されたブランチであってもブランチの再帰を停止するために使用できます。この関数は、p4est*search*localに類似して、任意のユーザー定義ポイントを検索するオプションを提供します。

!!! note
    プロセッサパーティション全体をトラバースするには少なくともO(P)かかるため、コールバック関数の賢明な使用が推奨され、短縮することができます。


### パラメータ

  * `p4est`:[in] トラバースするフォレスト。ローカルクアドラントには決してアクセスされません。
  * `call_post`:[in] trueの場合、クアドラントコールバックを前後で呼び出します。
  * `quadrant_fn`:[in] この関数は再帰を制御し、このコールバックがブランチクアドラントに対してtrueを返す場合にのみ、再帰が深く続きます。これをNULLに設定することも許可されています。
  * `point_fn`:[in] この関数は、各ポイントが再帰を下るかどうかを決定します。**points**がNULLでない場合、非NULLでなければなりません。
  * `points`:[in] コールバック**point_fn**に渡されるユーザー提供の**points**の配列。詳細についてはp8est*search*localを参照してください。

### プロトタイプ

```c
void p8est_search_partition (p8est_t * p4est, int call_post, p8est_search_partition_t quadrant_fn, p8est_search_partition_t point_fn, sc_array_t * points);
```
