function Model(;     iceflow::Union{IFM, Nothing},     mass_balance::Union{MBM, Nothing}     ) where {IFM <: IceflowModel, MBM <: MBmodel}

モデルをHuginnレベルで初期化します（機械学習モデルなし）。
