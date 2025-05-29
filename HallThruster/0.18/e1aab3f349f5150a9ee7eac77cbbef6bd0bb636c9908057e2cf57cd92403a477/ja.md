```julia
time_average(
    sol::HallThruster.Solution,
    start_time
) -> HallThruster.Solution{_A, _B, _C, S} where {_A, _B, _C, S<:(Vector)}

```

`Solution`を時間で平均化し、`start_time`から開始します。平均化されたシミュレーションプロパティを含む単一フレームの`Solution`オブジェクトを返します。
