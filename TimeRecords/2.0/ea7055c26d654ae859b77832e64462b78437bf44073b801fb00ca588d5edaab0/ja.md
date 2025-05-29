clampedbounds(ts::AbstractTimeSeries, t::Real, indhint=nothing)

findboundsのように動作しますが、常に時系列の境界内の整数境界を返します。境界外の結果は、下限を繰り返すか、上限を繰り返します。
