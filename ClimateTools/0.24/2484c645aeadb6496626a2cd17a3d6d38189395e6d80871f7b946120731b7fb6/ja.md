qqmap(obsvec::Array{N,1}, refvec::Array{N,1}, futvec::Array{N,1}, days, obs*jul, ref*jul, fut*jul; method::String="Additive", detrend::Bool=true, window::Int64=15, rankn::Int64=50, thresnan::Float64=0.1, keep*original::Bool=false, interp=Linear(), extrap=Flat())

単一ベクトルのための分位点-分位点マッピングバイアス補正。これはqqmap(A::ClimGrid ..)によって使用される低レベルの関数ですが、独立して動作することもできます。
