`refines(P,Q)` は `P` が `Q` の洗練であるかどうかを判断します。つまり、`P` のすべての部分が `Q` の部分のサブセットであるかどうかです。2つの分割は同じ基底集合を持っていなければならず、そうでない場合はエラーが発生します。

`refines(P,Q)` は `P<=Q` として呼び出すことができます。変種の `P<Q`、`P>=Q`、および `P>Q` は期待通りに動作します。分割は洗練によって部分的にのみ順序付けられていることに注意してください。`P<=Q` と `Q<=P` の両方が偽であるような分割 `P` と `Q` を簡単に構築することができます。
