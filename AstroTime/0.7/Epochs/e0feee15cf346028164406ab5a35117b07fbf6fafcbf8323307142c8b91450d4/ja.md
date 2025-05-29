```
TTEpoch(jd1::T, jd2::T=zero(T); origin=:j2000) where T<:AstroPeriod
```

ジュリア日付からTTEpochを構築します（オプションで`jd1`と`jd2`に分割可能）。`origin`は使用されるジュリア日付のバリアントを決定します。可能な値は次のとおりです：

  * `:j2000`: J2000ジュリア日付、`2000-01-01T12:00`から始まります
  * `:julian`: ジュリア日付、`-4712-01-01T12:00`から始まります
  * `:modified_julian`: 修正ジュリア日付、`1858-11-17T00:00`から始まります

### 例

```jldoctest; setup = :(using AstroTime)
julia> TTEpoch(0.0days, 0.5days)
2000-01-02T00:00:00.000 TT

julia> TTEpoch(2.451545e6days, origin=:julian)
2000-01-01T12:00:00.000 TT
```
