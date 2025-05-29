```julia
mutable struct BulkRecombination
```

バルク再結合を構築するために必要なすべての情報を保持する構造体。このコンストラクタを使用することで、ユーザーが選択した電子およびホールの準フェルミポテンシャルのインデックスを読み取ることができます。

  * `iphin::Int64`: 電子準フェルミポテンシャルのFVM構築のためのインデックス。
  * `iphip::Int64`: ホール準フェルミポテンシャルのFVM構築のためのインデックス。
  * `bulk_recomb_Auger::Bool`: バルク内のオージェ再結合の存在を示すブール値。
  * `bulk_recomb_radiative::Bool`: バルク内の放射再結合の存在を示すブール値。
  * `bulk_recomb_SRH::Union{Type{ChargeTransport.SRHOff}, Type{ChargeTransport.SRHStationary}, Type{ChargeTransport.SRHTrapsStationary}, Type{ChargeTransport.SRHTrapsTransient}}`: バルク内のSRH再結合のためのデータ型。これは、移動トラップの有無に関するケースのために型である必要があります。
  * `SRH_2species_trap::Union{Type{ChargeTransport.SRH2SpeciesPresentTrapDens}, Type{ChargeTransport.SRHOff}, Type{ChargeTransport.SRHStationary}}`: ポアソン方程式の右辺に定常トラップ密度を含めるためのデータ型。この定常トラップ密度は、占有されていないトラップ状態の数に対応します。
