```
(; A, B, C, D), simplified_sys = linearize(sys, inputs, outputs;    t=0.0, op = Dict(), allow_input_derivatives = false, zero_dummy_der=false, kwargs...)
(; A, B, C, D)                 = linearize(simplified_sys, lin_fun; t=0.0, op = Dict(), allow_input_derivatives = false, zero_dummy_der=false)
```

`sys`を`inputs`と`outputs`の間で線形化します。両方は変数のベクトルです。線形状態空間表現の行列を持つNamedTupleを返します。

$$
\begin{aligned}
ẋ &= Ax + Bu\\
y &= Cx + Du
\end{aligned}
$$

最初のシグネチャは内部で自動的に[`linearization_function`](@ref)を呼び出しますが、2番目のシグネチャは[`linearization_function`](@ref)の出力を入力として期待します。

`op`は線形化する周りの動作点を示します。提供されない場合、`sys`のデフォルト値が使用されます。

`allow_input_derivatives = false`の場合、入力導関数（$u̇$）が線形化された方程式の入力として現れるとエラーが発生します。入力導関数が許可されている場合、返される`B`行列は2倍の幅になり、入力`[u; u̇]`に対応します。

`zero_dummy_der`は、すべてのダミー導関数の動作点を自動的にゼロに設定するために設定できます。

さらに、より低レベルのインターフェースを提供する[`linearization_function`](@ref)、[`linearize_symbolic`](@ref)、および[`ModelingToolkit.reorder_unknowns`](@ref)も参照してください。

例については、拡張ヘルプを参照してください。

実装と表記は、["Linear Analysis Approach for Modelica Models", Allain et al. 2009](https://ep.liu.se/ecp/043/075/ecp09430097.pdf)に従っています。

# 拡張ヘルプ

この例は、次のフィードバック相互接続を構築し、`F`の入力から`P`の出力まで線形化します。

```

  r ┌─────┐       ┌─────┐     ┌─────┐
───►│     ├──────►│     │  u  │     │
    │  F  │       │  C  ├────►│  P  │ y
    └─────┘     ┌►│     │     │     ├─┬─►
                │ └─────┘     └─────┘ │
                │                     │
                └─────────────────────┘
```

```julia
using ModelingToolkit
using ModelingToolkit: t_nounits as t, D_nounits as D
function plant(; name)
    @variables x(t) = 1
    @variables u(t)=0 y(t)=0
    eqs = [D(x) ~ -x + u
           y ~ x]
    ODESystem(eqs, t; name = name)
end

function ref_filt(; name)
    @variables x(t)=0 y(t)=0
    @variables u(t)=0 [input = true]
    eqs = [D(x) ~ -2 * x + u
           y ~ x]
    ODESystem(eqs, t, name = name)
end

function controller(kp; name)
    @variables y(t)=0 r(t)=0 u(t)=0
    @parameters kp = kp
    eqs = [
        u ~ kp * (r - y),
    ]
    ODESystem(eqs, t; name = name)
end

@named f = ref_filt()
@named c = controller(1)
@named p = plant()

connections = [f.y ~ c.r # フィルタされた参照からコントローラの参照へ
               c.u ~ p.u # コントローラの出力からプラントの入力へ
               p.y ~ c.y]

@named cl = ODESystem(connections, t, systems = [f, c, p])

lsys0, ssys = linearize(cl, [f.u], [p.x])
desired_order = [f.x, p.x]
lsys = ModelingToolkit.reorder_unknowns(lsys0, unknowns(ssys), desired_order)

@assert lsys.A == [-2 0; 1 -2]
@assert lsys.B == [1; 0;;]
@assert lsys.C == [0 1]
@assert lsys.D[] == 0

## シンボリック線形化
lsys_sym, _ = ModelingToolkit.linearize_symbolic(cl, [f.u], [p.x])

@assert substitute(lsys_sym.A, ModelingToolkit.defaults(cl)) == lsys.A
```
