```julia
time_average(
    sol::HallThruster.Solution
) -> HallThruster.Solution{_A, _B, _C, S} where {_A, _B, _C, S<:(Vector)}
time_average(
    sol::HallThruster.Solution,
    start_frame::Integer
) -> HallThruster.Solution{_A, _B, _C, S} where {_A, _B, _C, S<:(Vector)}

```

時間にわたって `Solution` を平均化し、`start_frame` から開始します。平均化されたシミュレーションプロパティを含む単一のフレームを持つ `Solution` オブジェクトを返します。
