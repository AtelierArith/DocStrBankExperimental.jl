```
RiemannianProjectionBackend <: AbstractRiemannianDiffBackend
```

このバックエンドは、埋め込み内での微分を計算しますが、現在は勾配に制限されています。$mathcal M$を、いくつかの$R^m$に埋め込まれた多様体とし、$m$は通常（はるかに）多様体の次元より大きいとします。次の3つのツールが必要です。

  * 多様体に制限したときに関心のあるコスト関数$f$を生成する関数$f̃: ℝ^m → ℝ$。
  * 接ベクトルを埋め込みから接空間$T_p\mathcal M$に戻すための[`project`](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/projections.html#ManifoldsBase.project-Tuple{AbstractManifold,%20Any,%20Any})関数。これには、接ベクトルの表現の変更（例えば、リー代数内または異なるデータ形式での変更）も含まれます。
  * 非等長埋め込み多様体のための[`change_representer`](https://juliamanifolds.github.io/Manifolds.jl/stable/manifolds/metric.html#Manifolds.change_metric-Tuple{AbstractManifold,%20AbstractMetric,%20Any,%20Any})。つまり、埋め込みの接空間$T_pℝ^m$からの内積の制限を受け継がない多様体の接空間$T_p\mathcal M$です。

また、[`riemannian_gradient`](@ref)や[AbsilMahonySepulchre:2008](@cite)のセクション3.6.1を参照して、部分多様体に関する導出を確認してください。
