findbounds(ts::AbstractTimeSeries, t::Real)

t::Realの前後のTimeRecordのインデックスを二分法を使用して見つけます。tが時系列内にない場合、境界の1つはそのインデックス範囲に含まれません。範囲内の境界が必要な場合は、代わりにclampedbounds(ts, t, indhint)を使用してください。
