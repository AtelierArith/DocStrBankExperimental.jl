```
sigTable = SignalTable(args...)
```

Returns a new SignalTable dictionary.

Arguments `args...` are dictionary pairs where `values` must be [`Var`](@ref)(...) and/or [`Par`](@ref)(...) and/or [`Map`](@ref)(...). Example:

The *first* argument must define the *independent* signal, that is, `Var(values=..., independent=true), ...` and `values` must be an `AbstractVector`. Further added signals with a `:values` key, must have the same first dimension as the independent signal.

Most dictionary operations can be applied on `sigTable`, as well as all functions of [Overview of Functions](@ref).

# Examples

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

This results in the following output:

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

The command `show(IOContext(stdout, :compact => true), sigTable)` results in the following output:

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
