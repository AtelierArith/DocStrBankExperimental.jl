accumulate(ts::AbstractTimeSeries{T}; order=0) where T <: Number

時間系列をその時間間隔にわたって累積します。以下の順序オプションがあります：      (order=0) リーマン積分を使用する      (order=1) 台形積分を使用する
