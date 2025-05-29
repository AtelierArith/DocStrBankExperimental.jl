```julia
struct AnalysisPoint
```

```
AnalysisPoint(input, name::Symbol, outputs::Vector)
```

線形解析のためのAnalysisPointを作成します。分析ポイントは次のように呼び出すことで作成できます。

```
connect(out, :ap_name, in...)
```

ここで`out`は入力`in...`に接続される出力です。関与するすべてのコネクタ（入力および出力）は、未知数`u`を持つか、単一の未知数を持つ必要があり、すべて同じサイズである必要があります。

[`get_sensitivity`](@ref)、[`get_comp_sensitivity`](@ref)、[`get_looptransfer`](@ref)、[`open_loop`](@ref)も参照してください。

# フィールド

  * `input::Any`: 接続の入力。ModelingToolkitStandardLibrary.jlの文脈では、これは`RealOutput`コネクタです。
  * `name::Symbol`: 分析ポイントの名前。
  * `outputs::Union{Nothing, Vector{Any}}`: 接続の出力。ModelingToolkitStandardLibrary.jlの文脈では、これらはすべて`RealInput`コネクタです。

# 例

```julia
using ModelingToolkit
using ModelingToolkitStandardLibrary.Blocks
using ModelingToolkit: t_nounits as t

@named P = FirstOrder(k = 1, T = 1)
@named C = Gain(; k = -1)
t = ModelingToolkit.get_iv(P)

eqs = [connect(P.output, C.input)
       connect(C.output, :plant_input, P.input)]
sys = ODESystem(eqs, t, systems = [P, C], name = :feedback_system)

matrices_S, _ = get_sensitivity(sys, :plant_input) # (入力)感度関数の状態空間表現の行列を計算します。
matrices_T, _ = get_comp_sensitivity(sys, :plant_input)
```

制御システムベース.jlを使用して、引き続き線形解析と設計を行うことができます。次のように`ControlSystemsBase.StateSpace`オブジェクトを作成します。

```julia
using ControlSystemsBase, Plots
S = ss(matrices_S...)
T = ss(matrices_T...)
bodeplot([S, T], lab = ["S" "T"])
```

この方法で得られた感度関数は、以下のコードで得られたものと同等であるべきです。

```julia
using ControlSystemsBase
P = tf(1.0, [1, 1])
C = 1                      # ControlSystemsで負のフィードバックが仮定されています
S = sensitivity(P, C)      # またはfeedback(1, P*C)
T = comp_sensitivity(P, C) # またはfeedback(P*C)
```
