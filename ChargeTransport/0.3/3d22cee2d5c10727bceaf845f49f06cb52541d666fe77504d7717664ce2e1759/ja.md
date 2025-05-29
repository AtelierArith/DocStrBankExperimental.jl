```julia
mutable struct Data{TFuncs<:Function, TVoltageFunc<:Function, TGenerationData<:Union{Array{Float64, 3}, Function, VecOrMat{Float64}}}
```

すべてのデータ情報を保持する構造体で、モデルや数値情報だけでなく、半導体デバイスのドリフト-拡散シミュレーションに必要なすべての物理パラメータも含まれています。

  * `F::Vector{TFuncs} where TFuncs<:Function`: すべてのキャリア $\alpha$ に対する対応する分布関数 $\mathcal{F}_\alpha$ を持つ配列。
  * `qFModel::Union{Type{ChargeTransport.ContQF}, Type{ChargeTransport.DiscontQF}}`: 少なくとも1つの準フェルミポテンシャルが連続または不連続であると仮定されるかどうかの情報を含むデータ型。
  * `boundaryType::Vector{Union{Type{ChargeTransport.InterfaceNone}, Type{ChargeTransport.InterfaceRecombination}, Type{ChargeTransport.MixedOhmicSchottkyContact}, Type{ChargeTransport.OhmicContact}, Type{ChargeTransport.SchottkyBarrierLowering}, Type{ChargeTransport.SchottkyContact}}}`: 各境界（内部および外部）の境界モデルのタイプを持つデータ型の配列。
  * `contactVoltageFunction::Vector{TVoltageFunc} where TVoltageFunc<:Function`: 各外部境界での時間に依存する適用バイアスのための事前定義された関数を含む配列。
  * `bulkRecombination::ChargeTransport.BulkRecombination`: バルク再結合モデルに関する情報を含む構造体。
  * `generationData::Union{Array{Float64, 3}, Function, VecOrMat{Float64}}`: ユーザー特有の光生成率を含む関数/配列。ユーザーの例で指定された関数や、外部ソフトウェアで読み込まれ計算される配列である可能性があります。
  * `isContinuous::Vector{Bool}`: 電荷キャリアが連続か不連続かの情報を含む配列。これは、異なる領域の電荷キャリアのインデックスを処理するAbstractQuantitiesを構築するために必要です。
  * `chargeCarrierList::Vector{Union{Int64, VoronoiFVM.ContinuousQuantity{Int32}, VoronoiFVM.DiscontinuousQuantity{Int32}, VoronoiFVM.InterfaceQuantity{Int32}}}`: このリストは、VoronoiFVMに必要な正しいタイプのすべての電荷キャリアを格納します。
  * `electricCarrierList::Vector{Int64}`: このリストは、すべての電気キャリアインデックス、すなわち電子とホールのインデックスを格納します。
  * `ionicCarrierList::Vector{ChargeTransport.IonicCarrier}`: このリストは、すべての定義されたイオンキャリアをType IonicCarrierの構造体として含み、イオンキャリアに関するすべての必要な情報を持っています（イオンまたはイオン空孔のいずれか）。
  * `trapCarrierList::Vector{ChargeTransport.TrapCarrier}`: このリストは、SRH再結合のためのすべての定義されたトラップキャリアをType TrapCarrierの構造体として含み、トラップキャリアに関するすべての必要な情報を持っています。
  * `AuxTrapValues::ChargeTransport.AuxiliaryStationaryTrapValues`: 定常設定のための補助トラップ値を含む構造体。
  * `index_psi::Union{Int64, VoronoiFVM.ContinuousQuantity{Int32}, VoronoiFVM.DiscontinuousQuantity{Int32}, VoronoiFVM.InterfaceQuantity{Int32}}`: この変数は、電位のインデックスを格納します。ユーザーの選択に基づいて、この新しいタイプで不連続な未知数をシミュレートする機会があります。
  * `barrierLoweringInfo::ChargeTransport.BarrierLoweringSpecies`: ショットキー障壁低下をシミュレートするために必要なすべての情報を含む構造体。
  * `fluxApproximation::Vector{Union{Type{ChargeTransport.DiffusionEnhanced}, Type{ChargeTransport.DiffusionEnhancedModifiedDrift}, Type{ChargeTransport.ExcessChemicalPotential}, Type{ChargeTransport.ExcessChemicalPotentialGraded}, Type{ChargeTransport.GeneralizedSG}, Type{ChargeTransport.ScharfetterGummel}, Type{ChargeTransport.ScharfetterGummelGraded}}}`: フラックス離散化手法のためのデータ型。
  * `calculationType::Union{Type{ChargeTransport.InEquilibrium}, Type{ChargeTransport.OutOfEquilibrium}}`: 平衡または非平衡計算のためのデータ型。
  * `modelType::Union{Type{ChargeTransport.Stationary}, Type{ChargeTransport.Transient}}`: 過渡または定常計算のためのデータ型。
  * `generationModel::Union{Type{ChargeTransport.GenerationBeerLambert}, Type{ChargeTransport.GenerationNone}, Type{ChargeTransport.GenerationUniform}, Type{ChargeTransport.GenerationUserDefined}}`: 生成モデルのためのデータ型。
  * `λ1::Float64`: 非線形ポアソン問題を解くために使用される埋め込みパラメータ。ここで、λ1 = 0 の場合、右辺はゼロに設定され、λ1 = 1 の場合、完全な空間電荷密度があります。
  * `λ2::Float64`: 生成率のための埋め込みパラメータ。
  * `λ3::Float64`: 電気化学反応のための埋め込みパラメータ。
  * `ohmicContactModel::Union{Type{ChargeTransport.OhmicContactDirichlet}, Type{ChargeTransport.OhmicContactRobin}}`: 電位のオーム接触境界モデルの実装を変更する可能性（ディリクレまたはロビン）。
  * `tempBEE1::Vector{Float64}`: このテンプレート内には、各キャリアのバンドエッジエネルギーに関する情報がローカルに保存され、アロケーションを節約します。2点フラックス近似スキームのために、このようなテンプレートが2つあります。
  * `tempBEE2::Vector{Float64}`: tempBEE1の説明を参照してください。
  * `tempDOS1::Vector{Float64}`: このテンプレート内には、各キャリアの有効DOSに関する情報がローカルに保存され、アロケーションを節約します。2点フラックス近似スキームのために、このようなテンプレートが2つあります。
  * `tempDOS2::Vector{Float64}`: tempDOS2の説明を参照してください。
  * `params::ChargeTransport.Params`: すべての領域依存パラメータ情報を保持する構造体。詳細については、構造体Paramsを参照してください。
  * `paramsnodal::ChargeTransport.ParamsNodal`: すべての空間依存パラメータ情報を保持する構造体。詳細については、構造体ParamsNodalを参照してください。

```
