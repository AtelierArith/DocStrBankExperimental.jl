optimalbandwidth(k::HAC{T}, mm; prewhite::Bool=false) where {T<:Andrews} optimalbandwidth(k::HAC{T}, mm; prewhite::Bool=false) where {T<:NeweyWest}

AndrewsまたはNewey-Westに従って最適なバンド幅を計算します。
