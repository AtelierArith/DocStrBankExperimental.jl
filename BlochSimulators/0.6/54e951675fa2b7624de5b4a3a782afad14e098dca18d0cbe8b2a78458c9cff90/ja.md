```
SpokesTrajectory{T} <: AbstractTrajectory{T}
```

典型的なカルテジアンおよび放射状の軌道は多くの共通点があります：読み出しはk空間の開始点とサンプルポイントごとのΔkで記述できます。コードの繰り返しを避けるために、両方のタイプの軌道はSpokesTrajectoryのサブタイプとして作成され、そうでなければ両方の軌道に対して同じであるメソッドのいくつかはSpokesTrajectoryのために書かれています。
