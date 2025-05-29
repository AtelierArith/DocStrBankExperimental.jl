findbounds(ts::AbstractTimeSeries, t::Real, indhint::Base.RefValue{<:Integer})

t::Realの前後のTimeRecordのインデックスを見つけます。indhintは最初に検索されるインデックスです。以前の結果はindhintに保存され、順番に呼び出された場合に将来の呼び出しに対してヒットを提供します。tがタイムシリーズ内にない場合、境界の1つはそのインデックス範囲に含まれません。範囲内の境界が必要な場合は、代わりにclampedbounds(ts, t, indhint)を使用してください。
