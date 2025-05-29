```
showInfo([io::IO=stdout,] signalTable;
         sorted=false, showVar=true, showPar=true, showMap=true, showAttributes=true)
```

Writes info about a signal table to the output stream. The keyword arguments define what information shall be printed or whether the names shall be sorted or presented in definition order.

# Example

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

results in the following output

```julia
name          unit           size  eltypeOrType           kind attributes
───────────────────────────────────────────────────────────────────────────────────────────────────────
time          "s"            [6]   Float64                Var independent=true
load.r        "m"            [6,3] Float64                Var
motor.angle   "rad"          [6]   Float64                Var state=true, der="motor.w"
motor.w       "rad/s"        [6]   Float64                Var
motor.w_ref   ["rad", "1/s"] [6,2] Float64                Var info="Reference angle and speed"
wm            "rad/s"        [6]   Float64                Var alias="motor.w"
ref.clock                    [6]   Union{Missing,Bool}    Var variability="clock"
motor.w_c                    [6]   Union{Missing,Float64} Var variability="clocked", clock="ref.clock"
motor.inertia "kg*m/s^2"           Float32                Par
motor.data                         String                 Par
attributes                                                Map experiment=Map(stoptime=0.5, interval=0.01)
```
