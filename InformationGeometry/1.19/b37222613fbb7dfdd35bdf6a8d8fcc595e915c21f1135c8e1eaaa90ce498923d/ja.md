```
ComputeGeodesic(DM::DataModel, InitialPos::AbstractVector, InitialVel::AbstractVector, Endtime::Number=50.;
                                Boundaries::Union{Function,Nothing}=nothing, tol::Real=1e-11, approx::Bool=false, meth=Tsit5())
```

与えられた初期位置と速度で測地線を構築します。ブール値の関数 `Boundaries(u,t,int)` を指定することが可能で、これが `true` を返すときに積分プロセスが終了します。

キーワード `approx=true` を設定すると、クリストッフェル記号は定数であると仮定され、初期位置で一度だけ計算されます。これにより計算が非常に簡素化されますが、リッチ曲率の大きさによっては不正確な近似となる可能性もあります。
