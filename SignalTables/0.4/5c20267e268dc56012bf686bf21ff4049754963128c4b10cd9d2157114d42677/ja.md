```
sigTable = SignalTable(args...)
```

新しい SignalTable 辞書を返します。

引数 `args...` は辞書ペアであり、`values` は [`Var`](@ref)(...) および/または [`Par`](@ref)(...) および/または [`Map`](@ref)(...) でなければなりません。例：

*最初* の引数は *独立* 信号を定義する必要があります。すなわち、`Var(values=..., independent=true), ...` であり、`values` は `AbstractVector` でなければなりません。さらに追加された信号は `:values` キーを持ち、独立信号と同じ最初の次元を持たなければなりません。

ほとんどの辞書操作は `sigTable` に適用でき、[関数の概要](@ref) のすべての関数も適用できます。

# 例

```julia
using SignalTables
using Unitful

t = 0.0:0.1:0.5
sigTable = SignalTable(
  "time"         => Var(values= t, unit="s", independent=true),
  "load.r"       => Var(values= [sin.(t) cos.(t) sin.(t)], unit="m"),
  "motor.angle"  => Var(values= sin.(t), unit="rad", state=true, der="motor.w"),
  "motor.w"      => Var(values= cos.(t), unit="rad/s"),
  "motor.w_ref"  => Var(values= 0.9*[sin.(t) cos.(t)], unit = ["rad", "1/s"],
                                info="Reference angle and speed"),
  "wm"           => Var(alias = "motor.w"),
  "ref.clock"    => Var(values= [true, missing, missing, true, missing, missing],
                                 variability="clock"),
  "motor.w_c"    => Var(values= [0.8, missing, missing, 1.5, missing, missing],
                                variability="clocked", clock="ref.clock"),
  "motor.inertia"=> Par(value = 0.02f0, unit="kg*m/s^2"),
  "motor.data"   => Par(value = "resources/motorMap.json"),
  "attributes"   => Map(experiment=Map(stoptime=0.5, interval=0.01))
)

signalInfo(sigTable)
```

これにより、次の出力が得られます：

```julia
name          unit          size  eltypeOrType            kind attributes
─────────────────────────────────────────────────────────────────────────────────────────────────────────
time          "s"            [6]   Float64                Var  independent=true
load.r        "m"            [6,3] Float64                Var
motor.angle   "rad"          [6]   Float64                Var  state=true, der="motor.w"
motor.w       "rad/s"        [6]   Float64                Var
motor.w_ref   ["rad", "1/s"] [6,2] Float64                Var  info="Reference angle and speed"
wm            "rad/s"        [6]   Float64                Var  alias="motor.w"
ref.clock                    [6]   Union{Missing,Bool}    Var  variability="clock"
motor.w_c                    [6]   Union{Missing,Float64} Var  variability="clocked", clock="ref.clock"
motor.inertia "kg*m/s^2"           Float32                Par
motor.data                         String                 Par
attributes                                                Map  experiment=Map(stoptime=0.5, interval=0.01)
```

コマンド `show(IOContext(stdout, :compact => true), sigTable)` は次の出力を生成します：

```julia
SignalTable(
  "time" => Var(values=0.0:0.1:0.5, unit="s", independent=true),
  "load.r" => Var(values=[0.0 1.0 0.0; 0.0998334 0.995004 0.0998334; 0.198669 0.980067 0.198669; 0.29552 0.955336 0.29552; 0.389418 0.921061 0.389418; 0.479426 0.877583 0.479426], unit="m"),
  "motor.angle" => Var(values=[0.0, 0.0998334, 0.198669, 0.29552, 0.389418, 0.479426], unit="rad", state=true. der="motor.w"),
  "motor.w" => Var(values=[1.0, 0.995004, 0.980067, 0.955336, 0.921061, 0.877583], unit="rad/s"),
  "motor.w_ref" => Var(values=[0.0 0.9; 0.0898501 0.895504; 0.178802 0.88206; 0.265968 0.859803; 0.350477 0.828955; 0.431483 0.789824], unit=["rad", "1/s"], info="Reference angle and speed"),
  "wm" => Var(values=[1.0, 0.995004, 0.980067, 0.955336, 0.921061, 0.877583], unit="rad/s", alias="motor.w"),
  "ref.clock" => Var(values=Union{Missing, Bool}[true, missing, missing, true, missing, missing], variability="clock"),
  "ref.trigger" => Var(values=Union{Missing, Bool}[missing, missing, true, missing, true, true], variability="trigger"),
  "motor.w_c" => Var(values=Union{Missing, Float64}[0.8, missing, missing, 1.5, missing, missing], variability="clocked", clock="ref.clock"),
  "motor.inertia" => Par(value=0.02, unit="kg*m/s^2"),
  "motor.data" => Par(value="resources/motorMap.json"),
  "attributes" => Map(experiment=Map(stoptime=0.5, interval=0.01)),
  )
```
