```julia
struct Scenario{F,P,M} <: AbstractScenario
    init_func::F
    prob::P
    measurements::M
    tags::AbstractVector{Symbol}
    group::Union{Symbol,Nothing}
    parameters::NamedTuple
end

シミュレーション条件を表す型、すなわち、更新されたパラメータと出力を持つモデルのバリアント。

内部プロパティを取得するには、メソッドを使用します: `tspan(scenario)`, `parameters(scenario)`, `measurements(scenario)`
```
