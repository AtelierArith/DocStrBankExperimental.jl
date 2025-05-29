```
ShootingInverseRetraction <: ApproximateInverseRetraction
```

射撃法を使用して再tractionの逆を近似します。

この射撃法の実装は、別の逆再tractionを使用してベクトルの最初の推測を形成することによって機能します。この推測は、ベクトルを射撃し、射撃結果からターゲットポイントへのベクトルを推測し、このベクトルの更新を離散化されたグリッド上の初期点に戻すことによって更新されます。このプロセスは、ベクトルの更新のノルムが指定された許容範囲を下回るか、最大反復回数に達するまで繰り返されます。

# フィールド

  * `retraction::AbstractRetractionMethod`: 逆が近似される再traction。
  * `initial_inverse_retraction::AbstractInverseRetractionMethod`: ベクトルの初期推測を形成するために使用される逆再traction。
  * `vector_transport::AbstractVectorTransportMethod`: ベクトルの初期推測を輸送するために使用されるベクトル輸送。
  * `num_transport_points::Int`: 射撃法におけるベクトル輸送に使用される離散化ポイントの数。2は、端点のみを含む最小ポイント数です。
  * `tolerance::Real`: 射撃法の許容範囲。
  * `max_iterations::Int`: 射撃法の最大反復回数。
