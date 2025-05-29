```julia
mutable struct Data{TFuncs<:Function, TVoltageFunc<:Function, TGenerationData<:Union{Array{Float64, 3}, Function, VecOrMat{Float64}}}
```

A struct holding all data information including model and numerics information, but also all physical parameters for a drift-diffusion simulation of a semiconductor device.

  * `F::Vector{TFuncs} where TFuncs<:Function`: An array with the corresponding distribution function $\mathcal{F}_\alpha$ for all carriers $\alpha$.

  * `qFModel::Union{Type{ChargeTransport.ContQF}, Type{ChargeTransport.DiscontQF}}`: An datatype containing the information, whether at least on quasi Fermi potential is assumed to be continuous or discontinuous.

  * `boundaryType::Vector{Union{Type{ChargeTransport.InterfaceNone}, Type{ChargeTransport.InterfaceRecombination}, Type{ChargeTransport.MixedOhmicSchottkyContact}, Type{ChargeTransport.OhmicContact}, Type{ChargeTransport.SchottkyBarrierLowering}, Type{ChargeTransport.SchottkyContact}}}`: An array of DataTypes with the type of boundary model for each boundary (interior and exterior).

  * `contactVoltageFunction::Vector{TVoltageFunc} where TVoltageFunc<:Function`: An array containing predefined functions for the applied bias in dependence of time at each outer boundary.

  * `bulkRecombination::ChargeTransport.BulkRecombination`: A struct containing information concerning the bulk recombination model.

  * `generationData::Union{Array{Float64, 3}, Function, VecOrMat{Float64}}`: A function/Array containing the user-specific photogeneration rate. It can be a function which is specified in the user example or an array which is read in and calculated with, e.g., an external software.

  * `isContinuous::Vector{Bool}`: An array containing information on whether charge carriers are continuous or discontinuous. This is needed for building the AbstractQuantities which handle the indices of charge carriers on different regions.

  * `chargeCarrierList::Vector{Union{Int64, VoronoiFVM.ContinuousQuantity{Int32}, VoronoiFVM.DiscontinuousQuantity{Int32}, VoronoiFVM.InterfaceQuantity{Int32}}}`: This list stores all charge carriers with the correct type needed for VoronoiFVM.

  * `electricCarrierList::Vector{Int64}`: This list stores all electric carrier indices, i.e. the one of electrons and holes.

  * `ionicCarrierList::Vector{ChargeTransport.IonicCarrier}`: This list contains all defined ionic carriers as a struct of Type IonicCarrier with all needed information on the ionic carriers (can be either ions or ion vacancies).

  * `trapCarrierList::Vector{ChargeTransport.TrapCarrier}`: This list contains all defined trap carriers for the SRH recombination as a struct of Type TrapCarrier with all needed information on the trap carriers.

  * `AuxTrapValues::ChargeTransport.AuxiliaryStationaryTrapValues`: A struct which contains auxiliary trap values for the stationary setting.

  * `index_psi::Union{Int64, VoronoiFVM.ContinuousQuantity{Int32}, VoronoiFVM.DiscontinuousQuantity{Int32}, VoronoiFVM.InterfaceQuantity{Int32}}`: This variable stores the index of the electric potential. Based on the user choice we have with this new type the opportunity to simulate discontinuous unknowns.

  * `barrierLoweringInfo::ChargeTransport.BarrierLoweringSpecies`: This is a struct containing all information necessary to simulate Schottky Barrier Lowering.

  * `fluxApproximation::Vector{Union{Type{ChargeTransport.DiffusionEnhanced}, Type{ChargeTransport.DiffusionEnhancedModifiedDrift}, Type{ChargeTransport.ExcessChemicalPotential}, Type{ChargeTransport.ExcessChemicalPotentialGraded}, Type{ChargeTransport.GeneralizedSG}, Type{ChargeTransport.ScharfetterGummel}, Type{ChargeTransport.ScharfetterGummelGraded}}}`: A DataType for the flux discretization method.

  * `calculationType::Union{Type{ChargeTransport.InEquilibrium}, Type{ChargeTransport.OutOfEquilibrium}}`: A DataType for equilibrium or out of equilibrium calculations.

  * `modelType::Union{Type{ChargeTransport.Stationary}, Type{ChargeTransport.Transient}}`: A DataType for transient or stationary calculations.

  * `generationModel::Union{Type{ChargeTransport.GenerationBeerLambert}, Type{ChargeTransport.GenerationNone}, Type{ChargeTransport.GenerationUniform}, Type{ChargeTransport.GenerationUserDefined}}`: A DataType for for generation model.

  * `λ1::Float64`: An embedding parameter used to solve the nonlinear Poisson problem, where for λ1 = 0 the right hand-side is set to zero whereas for for λ1 = 1 we have a full space charge density.

  * `λ2::Float64`: An embedding parameter for the generation rate.

  * `λ3::Float64`: An embedding parameter for an electrochemical reaction.

  * `ohmicContactModel::Union{Type{ChargeTransport.OhmicContactDirichlet}, Type{ChargeTransport.OhmicContactRobin}}`: Possibility to change the implementation of the ohmic contact boundary model for the electric potential (Dirichlet or Robin)

  * `tempBEE1::Vector{Float64}`: Within this template, information concerning the band-edge energy of each carrier is stored locally which saves allocations. We have two of such templates due to the two point flux approximation schemes.

  * `tempBEE2::Vector{Float64}`: See the description of tempBEE1.

  * `tempDOS1::Vector{Float64}`: Within this template, information concerning the effective DOS of each carrier is stored locally which saves allocations. We have two of such templates due to the two point flux approximation schemes.

  * `tempDOS2::Vector{Float64}`: See the description of tempDOS2.

  * `params::ChargeTransport.Params`: A struct holding all region dependent parameter information. For more information see struct Params.

  * `paramsnodal::ChargeTransport.ParamsNodal`: A struct holding all space dependent parameter information. For more information see struct ParamsNodal.
