```
feedback(sys1::AbstractStateSpace, sys2::AbstractStateSpace;
         U1=:, Y1=:, U2=:, Y2=:, W1=:, Z1=:, W2=Int[], Z2=Int[],
         Wperm=:, Zperm=:, pos_feedback::Bool=false)
```

*基本的な使い方* `feedback(sys1, sys2)` は（負の）フィードバック相互接続を形成します。

```julia
           ┌──────────────┐
◄──────────┤     sys1     │◄──── Σ ◄──────
    │      │              │      │
    │      └──────────────┘      -1
    │                            |
    │      ┌──────────────┐      │
    └─────►│     sys2     ├──────┘
           │              │
           └──────────────┘
```

第二のシステム `sys2` が指定されていない場合、負の単位フィードバック（`sys2 = 1`）が仮定されます。返される閉ループシステムは、`sys1` の状態の後に `sys2` の状態が続く状態ベクトルを持ちます。

*高度な使い方* `feedback` は、以下の図に従ってより柔軟な使用もサポートしています。

```julia
              ┌──────────────┐
      z1◄─────┤     sys1     │◄──────w1
 ┌─── y1◄─────┤              │◄──────u1 ◄─┐
 │            └──────────────┘            │
 │                                        α
 │            ┌──────────────┐            │
 └──► u2─────►│     sys2     ├───────►y2──┘
      w2─────►│              ├───────►z2
              └──────────────┘
```

  * `U1`, `W1` は、`u1` および `w1` に対応する `sys1` の入力信号のインデックスを指定します。`W1` には、返されるシステムの入力に含まれる `sys1` の入力のインデックスが含まれます。すなわち、外部入力です。
  * `Y1`, `Z1` は、`y1` および `z1` に対応する `sys1` の出力信号のインデックスを指定します。`Z1` には、返されるシステムの出力に含まれる `sys1` の出力のインデックスが含まれます。すなわち、外部出力です。
  * `U2`, `W2`, `Y2`, `Z2` は、`sys2` の対応する信号を指定します。`W2` には、返されるシステムの入力に含まれる `sys2` の入力のインデックスが含まれます。すなわち、外部入力です。`Z2` には、返されるシステムの出力に含まれる `sys2` の出力のインデックスが含まれます。すなわち、外部出力です。

`Wperm` と `Zperm` を指定して、結果の状態空間モデルにおける入力（[w1; w2] に対応）と出力（[z1; z2] に対応）を再配置します。

負のフィードバック（α = -1）がデフォルトです。正のフィードバック（α = 1）を指定するには `pos_feedback=true` を使用します。

`lft`, `starprod`, `sensitivity`, `input_sensitivity`, `output_sensitivity`, `comp_sensitivity`, `input_comp_sensitivity`, `output_comp_sensitivity`, `G_PS`, `G_CS` も参照してください。

マニュアルセクション [From block diagrams to code](https://juliacontrol.github.io/ControlSystems.jl/stable/man/creating_systems/#From-block-diagrams-to-code) には、この関数の使用方法に関する高レベルの指示が含まれています。また、[RobustAndOptimalControl.jl: Connections using named signals](https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/#Connecting-systems-together) も高レベルのインターフェースについて参照してください。

Zhou, Doyle, Glover (1996) の類似の（やや対称性の少ない）公式についても参照してください。
