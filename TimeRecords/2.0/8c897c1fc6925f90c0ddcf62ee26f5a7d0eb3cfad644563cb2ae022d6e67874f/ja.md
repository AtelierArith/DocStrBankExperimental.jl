findbounds(ts::AbstractTimeSeries, t::Real, indhint::Integer)

t::Real の前後の TimeRecord のインデックスを見つけます; indhint は検索を開始する最初のインデックスです。t がタイムシリーズ内にない場合、境界の一方はそのインデックス範囲に含まれません。範囲内の境界が必要な場合は、代わりに clampedbounds(ts, t, indhint) を使用してください。
