```
spectraldistances_trace(usv::SVD; onrows=true, groups=nothing, alpha=1.0, q=0.5)
spectraldistances_trace(vecs, vals, groups)
```

は、スペクトルの各パーティションと各タクサのペア内でスペクトル残差を計算します。

行がスペクトルパーティションで、列がタクサ:タクサペアである行列を返します。これは、行ごとの順序で上三角、または列ごとの順序で下三角に並べられています。

引数:

  * メソッド: `spectraldistances_trace(vecs, vals, groups)`

      * vecs: usv.U または usv.V 行列
      * vals: usv.S 特異値ベクトル
      * groups: 通常は `getintervals(usv.S; alpha=alpha, q=q)` で計算されます
  * メソッド: `spectraldistances_trace(usv::SVD; onrows=true, groups=nothing, alpha=1.0, q=0.5)`     

      * usv: SVD オブジェクト
      * onrows: 行（U 行列）または列（V 行列）でスペクトル距離を計算するための true/false スイッチ。
      * groups: 何も指定しない場合、`getintervals(usv.S; alpha=alpha, q=q)` でグループが計算されます。そうでない場合は、`usv.S` をグループ化するためのインデックス範囲のベクトル `[1:1, 2:3, ...]` を仮定します。
      * alpha: `getintervals` に渡されます
      * q: `getintervals` に渡されます
