function Model(;     iceflow::Union{IFM, Nothing},     mass_balance::Union{MBM, Nothing}     ) where {IFM <: IceflowModel, MBM <: MBmodel}

Initialize Model at Huginn level (no machine learning model).
